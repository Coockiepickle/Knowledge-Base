## Installation Docker

`sudo apt update && sudo apt install -y ca-certificates curl gnupg lsb-release`

---

## Ajout de la clé GPG

```bash
sudo install -m 0755 -d /etc/apt/keyrings
curl -fsSL https://download.docker.com/linux/debian/gpg | \
  sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg
```

---

## Ajout du dépôt officiel

```bash
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] \
  https://download.docker.com/linux/debian $(lsb_release -cs) stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null
```

```bash
sudo apt update
sudo apt install -y docker-ce docker-ce-cli containerd.io \
docker-buildx-plugin docker-compose-plugin
```

---

## Démarrage et vérification

```bash
sudo systemctl enable --now docker
sudo docker run --rm hello-world
docker compose version
```

---

## Allow user to run Docker without sudo

```bash
sudo usermod -aG docker "$USER"
newgrp docker
```