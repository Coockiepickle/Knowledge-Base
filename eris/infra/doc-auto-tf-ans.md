## Documentation - Stack Web automatisée

### Terraform + Ansible + Nginx Reverse Proxy + Pipeline Jenkins/Gitea


Minikube local · Gitea `192.168.1.37:3000` · Jenkins `192.168.1.37:8080`

---

## 1. Gitea - Les 3 dépôts

### 1.1 Vue d'ensemble des dépôts

Les 3 dépôts créés dans l'espace utilisateur `std` sur Gitea  :


---

### 1.2 Dépôt `terraform-infra`

Il contient tout le code Terraform pour la VM et les services Kubernetes  :


| Fichier | Rôle                                                                  |
| :-------- | :----------------------------------------------------------------------- |
| `providers.tf`        | Déclare le provider `hashicorp/kubernetes` et pointe sur le contexte `minikube`                       |
| `main.tf`        | Crée le namespace `webstack`, le Deployment Debian (VM), et le Service NodePort |
| `outputs.tf`        | Exporte les ports et l'IP Minikube utilisés par les étapes suivantes |

---

### 1.3 Dépôt `ansible-config`

Contient les playbooks Ansible pour configurer la VM provisionnée par Terraform  :


| Fichier | Rôle                                                                           |
| :-------- | :-------------------------------------------------------------------------------- |
| `playbook.yml`        | Installe Nginx, déploie la page web, s'assure que le service est actif au boot |
| `inventory.ini`        | Inventaire avec placeholder `MINIKUBE_IP` remplacé par le pipeline                          |
| `templates/index.html.j2`        | Template Jinja2 de la page web personnalisée (Perplexity)                      |

---

### 1.4 Dépôt `proxy-deploy` - Dépôt principal

Il est pointé par Jenkins :


| Fichier | Rôle                                                    |
| :-------- | :--------------------------------------------------------- |
| `nginx.conf`        | Conf du reverse proxy avec placeholder `VM_IP`                  |
| `docker-compose.yml`        | Lance le container `nginx:alpine` en mode reverse proxy sur le port 80 |
| `Jenkinsfile`        | Définition du pipeline CI/CD                            |

---

### 1.5 Le Jenkinsfile dans Gitea

Le `Jenkinsfile` stocké dans `proxy-deploy` :


Les premières lignes définissent les variables d'environnement vers les 3 repos Gitea :

```groovy
environment {
    GITEA_BASE   = 'http://192.168.1.37:3000/std'
    TF_REPO      = 'terraform-infra'
    ANSIBLE_REPO = 'ansible-config'
    PROXY_REPO   = 'proxy-deploy'
    SSH_KEY_ID   = 'ansible-ssh-key'
}
```

---

## 2. Jenkins - Configuration du job

### 2.1 Paramètres généraux du job

La section "Pipeline" sur la page de configuration du job `devops-stack-pipeline`  :



| Paramètre | Valeur |
| :----------- | :------- |
| **Definition**           | `Pipeline script from SCM`       |
| **SCM**           | `Git`       |
| **Repository URL**           | `http://192.168.1.37:3000/std/proxy-deploy.git`       |
| **Branch Specifier**           | `*/main`       |
| **Script Path**           | `Jenkinsfile`       |

⚠️ Il faut choisir  **&quot;Pipeline script from SCM&quot;**  : Jenkins va chercher le `Jenkinsfile` directement dans Gitea à chaque build, pour que le pipeline soit toujours synchronisé.


---

## 3. Description des 7 étapes du pipeline

### Étape 1 - Checkout

Clone les 3 repos depuis Gitea dans des sous-dossiers du workspace Jenkins :

* `proxy-deploy` → racine
* `terraform-infra` → `./terraform/`
* `ansible-config` → `./ansible/`

### Étape 2 - Validaate

`terraform validate` + `terraform fmt -check` → vérifie la syntaxe HCL

`ansible-playbook --syntax-check` → vérifie la syntaxe YAML

### Étape 3 - Apply

```bash
terraform init
terraform plan -out=tfplan
terraform apply -auto-approve tfplan
MINIKUBE_IP=$(minikube ip)
echo "MINIKUBE_IP=${MINIKUBE_IP}" > ../deploy.env
```

Crée le Pod Debian (VM Linux) avec ses services. IP dans `deploy.env`

### Étape 4 - Generate Inventory

Remplace le placeholder `MINIKUBE_IP` dans `inventory.ini` :

```bash
sed -i "s/MINIKUBE_IP/${MINIKUBE_IP}/g" inventory.ini
```

### Étape 5 - Ansible Configure

Lance le playbook sur la VM :

```bash
ansible-playbook -i inventory.ini \
    --private-key "$SSH_KEY_FILE" \
    --user "$SSH_USER" \
    playbook.yml -v
```

### Étape 6 - Deploy Reverse Proxy

Entre l'IP dans `nginx.conf` puis lance le container :

```bash
sed -i "s/VM_IP/${MINIKUBE_IP}/g" nginx.conf
docker compose up -d --force-recreate
```

### Étape 7 - Test

Vérif avec `curl` à travers le reverse proxy :

```bash
STATUS=$(curl -s -o /tmp/body.html -w "%{http_code}" http://${MINIKUBE_IP}:80)
```

Il faut vérifier que l'on obtnient "HTTP 200" et "Secure Web Stack" dans le body


---

## 4. Credential SSH requis dans Jenkins

Avant la 1ère éxécution, ajouter le credential SSH dans :
Manage Jenkins → Credentials → System → Global → Add Credentials

|             |                                                |
| :------------ | :----------------------------------------------- |
| Kind        | `SSH Username with private key`                                               |
| ID          | `ansible-ssh-key`                                               |
| Username    | `root`                                               |
| Private Key | Clé privée SSH du serveur Jenkins vers la VM |

---

## 5. Lancer le pipeline

Sur le job `devops-stack-pipeline` dans Jenkins  :


1. Cliquer sur  **&quot;Build Now&quot;**  dans le menu gauche
2. Suivre l'exécution dans  **&quot;Build History&quot;**  puis les logs de chaque étape
3. En cas de succès, affiche :

SUCCESS: custom page served correctly through reverse proxy!

> Pour le moment, mon stack ne fonctionne pas, donc pas de capture d'écran du résultat :(

---

## 6.Détruire

Pour supprimer toute la stack :

```bash
cd proxy-deploy/
docker compose down

cd terraform/
terraform destroy -auto-approve
```

Ou fazire un job Jenkins dédié `destroy` avec `when: manual` pour détruire en un clic depuis l'interface.