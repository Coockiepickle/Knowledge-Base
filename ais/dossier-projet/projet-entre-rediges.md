## <font color="#92d050">Projet 1 : Modernisation de l'infrastructure réseau</font>

### 1. Compétences mises en œuvre

J'ai mobilisé plusieurs compétences pour mener à bien ce projet :
- Administration et sécurisation des infrastructures systèmes,
- Administration et sécurisation des infrastructures réseaux,
- Conception d'une solution technique répondant aux besoins d’évolution de l'infrastructure,
- Mise en production des évolutions de l’infrastructure,
- Application des bonnes pratiques dans l’administration des infrastructures.

### 2. Cahier des charges / Expression des besoins

En 2024, le DSI a fait appel à BPI France pour realiser un audit de sécurité. Le score de l'audit était vraiment bas. Puisque mes parents habitent proche de Meta Laser, on m'a chargé d'augmenter le score de BPI France en suivant leurs recommendations. L'objectif principal du projet était d'améliorer la sécurité et l'organisation de l'infrastructure réseau. J'ai travaillé à rendre l'infrastructure plus propre et mieux centralisée, tout en garantissant un accès sécurisé aux serveurs. J'ai également modernisé l'installation en supprimant les anciens équipements obsolètes et en réduisant leur nombre afin d’optimiser l'espace et la gestion du réseau. J'ai éliminé les équipements non utilisés ou non manageables et restreint l'accès aux équipements. Enfin, j'ai facilité la transition d'un stockage local vers un stockage unique à toutes les entreprises sur le cloud.

![[20241017_124509.jpg]]
![[20241017_165434.jpg]]
![[20241018_144601.jpg]]
### 3. Gestion de projet

J'ai planifié les tâches à l'aide de l'outil Plane, ce qui m'a permis un suivi structuré des différentes étapes. J'ai organisé le placement des équipements dans la baie en réalisant une simulation avec Packet Tracer. Pour minimiser l'impact sur les utilisateurs, j'ai effectué toutes les interventions après leur départ, garantissant ainsi une continuité de service optimale. Avant de mettre en œuvre les modifications, j'ai présenté un plan d'action détaillé au  DSI pour validation.
Après m'être occupé de la partie réseau, je me suis concentré sur l'aspect cybersécurité de l'usine. J'ai commencé par mettre à jour tous les ordinateurs ainsi que supprimé toutes les applications futiles et piratées. J'ai ensuite installé un gestionnaire de mots de passe sécurisé pour chaque utilisateur avec une petite formation sur la difficulté des mots de passe. Après avoir mis en place les gestionnaires, j’y ai importé les mots de passe des utilisateurs et désactivé l'enregistrement dans les navigateurs.
J'ai aussi déplacé tous les fichiers stockés localement vers le stockage cloud du groupe, ce qui a été le plus compliqué pour cette partie, c'est qu’il y a, pour une grande partie des fichiers, des appels dans la base de données de l'entreprise. J'ai donc parcouru toutes les tables de la BDD pour modifier les chemins réseau, pour passer de A:\ vers B:\.

### 4. Choix des solutions et critères de sélection

J'ai choisi Plane pour la gestion du projet en raison de sa simplicité d'utilisation, de sa gratuité et de son efficacité comme alternative à Trello. Pour modéliser l'organisation des équipements dans la baie avant toute modification physique, j'ai utilisé Packet Tracer. Cette approche m'a permis de mieux planifier l'espace et d'éviter les erreurs liées à un manque de place. J'ai choisi Bitwarden comme gestionnaire de mots de passe car c'est ce que j'utilise personnellement, il est reconnu comme étant très sécurisé et assez simple d'utilisation.

### 5. Organisation de la mise en œuvre

J'ai commencé par analyser en détail le réseau et élaborer une procédure précise pour le déplacement des serveurs.

Pour éviter tout risque de perte de données et limiter les interruptions, j'ai effectué les opérations en dehors des horaires de travail, une fois le personnel parti. Grâce à cette organisation, la transition vers la nouvelle infrastructure s'est déroulée de manière fluide et sécurisée.

J'ai rencontré quelques difficultés lors du déplacement des boîtiers de fibre dans le faux plafond afin de les amener dans la baie, mais j'ai réussi à les surmonter sans impact majeur sur le projet.

J'ai également passé une commande de matériel informatique que j'ai préalablement choisi par rapport à nos besoins. J'ai installé et configuré plusieurs switches, le compte administrateur et leurs VLANs.

J'ai participé à l'intégration du VLAN de production, regroupant toutes les machines de découpe et de pliage. Ce sous-réseau était auparavant quasiment totalement séparé du réseau, très instable et sans analyse du trafic ni possibilité de gestion.

Toutes ces tâches m'ont permis de mettre à jour le parc informatique de Meta Laser, mais aussi la facilité d'administration avec les switches manageables. Le fait qu'ils soient compatibles PoE nous permet de retirer plusieurs injecteur et d'avoir moins de câbles.

### 6. Relations avec les principaux acteurs du projet

J'ai collaboré étroitement avec le DSI et l'administrateur Systèmes et Réseaux, qui ont validé les différentes étapes et m'ont aidé à déplacer les équipements vers la baie. Leur implication a permis d'assurer que les changements effectués étaient conformes aux attentes.

### 7. Synthèse et conclusion

Grâce à ce projet, j'ai renforcé mes compétences en administration réseau et en gestion de projet. J'ai aussi contribué activement à l'amélioration de l'infrastructure informatique en appliquant des solutions efficaces et en garantissant une transition sécurisée.

## <font color="#92d050">Projet 2 : Développement d'un outil de revue de droits</font>

### 1. Compétences mises en œuvre

J'ai mobilisé plusieurs compétences pour mener à bien ce projet :
- Mesurer et analyser le niveau de sécurité de l'infrastructure,
- Détecter et traiter les incidents de sécurité,
- Élaborer et mettre en œuvre la politique de sécurité.

### 2. Cahier des charges / Expression des besoins

L'objectif du projet était de surveiller efficacement les changements des droits d'accès aux ressources informatiques. J'ai mis en place un suivi détaillé des modifications par entreprise et par période afin d'identifier rapidement d'éventuelles anomalies. J'ai développé l'outil entièrement en interne pour garantir un contrôle total sur son fonctionnement et sa sécurité. J'ai également conçu un tableau permettant d'afficher clairement les données collectées afin de faciliter leur lecture et leur analyse.

> Mettre les scripts avec des screens des résultats 

### 3. Gestion de projet

Pour structurer le projet, j'ai d'abord proposé un langage de programmation à mon tuteur afin de m'assurer qu'il correspondait aux objectifs. Avant de commencer le développement, j'ai présenté une solution détaillée pour validation. J'ai réalisé les tests en plusieurs étapes : d'abord sur une machine virtuelle, puis sur un serveur de test, avant d'effectuer les tests finaux pour m'assurer du bon fonctionnement de l'outil en conditions réelles.

### 4. Choix des solutions et critères de sélection

J'ai choisi PowerShell comme langage de développement, car il permet d'interagir directement avec Active Directory et d'exécuter des commandes adaptées à la récupération des droits d'accès. Pour optimiser le stockage, j'ai enregistré les données dans un fichier CSV, un format léger qui facilite la manipulation des informations. Enfin, j'ai opté pour un affichage des résultats sous forme de tableau HTML, ce qui améliore la lisibilité et permet une personnalisation pour une visualisation plus efficace.

### 5. Organisation de la mise en œuvre

J'ai commencé par demander à plusieurs IA de générer des scripts PowerShell en fonction du cahier des charges. Après avoir testé ces scripts sur deux serveurs de test (une VM locale puis une VM de test), j'ai combiné les parties les plus utiles et fonctionnelles en un seul script. J'ai ensuite effectué plusieurs tests, réalisé une démonstration à mon tuteur et modifié certains éléments selon ses recommandations.

J'ai rencontré plusieurs obstacles durant la réalisation de ce projet, notamment la gestion des chemins réseau dépassant parfois 256 caractères et la lenteur d'exécution du script en raison du nombre très élevé de dossiers à analyser.

### 6. Relations avec les principaux acteurs du projet

J'ai effectué des vérifications fréquentes avec mon tuteur afin de m'assurer que je ne m'éloignais pas de l'objectif principal.

### 7. Synthèse et conclusion

Ce projet m'a permis de renforcer mes compétences en développement, en administration système et en sécurité. J'ai mis en place une solution efficace pour le suivi des changements des droits d'accès, tout en améliorant ma capacité à résoudre des problèmes techniques complexes.

## <font color="#92d050">Projet 3 : Serveur d'impression</font>

### 1. Compétences mises en œuvre

J'ai mobilisé plusieurs compétences pour mener à bien ce projet :
- Administrer et sécuriser les infrastructures virtualisées 
- Mettre en production des évolutions de l’infrastructure 
- Participer à l’élaboration et à la mise en œuvre de la politique de sécurité

### 2. Cahier des charges / Expression des besoins

Le but de ce projet était de mettre en place un serveur d'impression sous Windows Server afin d'enlever ce rôle à la machine Active Directory. Pour un souci de sécurité, il est préférable que le serveur Active Directory n'est pas d'autre rôle afin d'ouvrir le moins de port et donc d'être moins vulnérable. 

On m'a donc demandé de mettre en place une machine virtuelle Windows Server avec le rôle serveur d'impression. J'ai également dû ajouter manuellement tous les pilotes et les imprimantes afin d'afin les dernières versions et les bonnes informations de connexion.

### 3. Gestion de projet


### 4. Choix des solutions et critères de sélection
Nous avons choisi de mettre en place le serveur d'impression sur Windows Server pour plusieurs raisons : 
- Des stratégies de groupe peuvent être utilisées pour gérer les imprimantes et leurs accès,
- Windows Server intègre l'outil de gestion de l'impression, qui est très facile à installer et utiliser. Il permet de surveiller l'état des imprimantes, de gérer les pilotes, de suivre les travaux d'impression et de contrôler les accès,
- Les autorisations peuvent être définies avec précision pour chaque utilisateur ou groupe,
- Windows Server propose des fonctionnalités avancées telles que la mise en file d'attente des impressions, la gestion des priorités et la possibilité de configurer des pools d'imprimantes pour une meilleure disponibilité,
- Windows est plus stable pour gérer un grand nombre d'imprimantes sur des réseaux différents, ce qui est notre cas.

### 5. Organisation de la mise en œuvre

#### Création de la VM dans VMWare

1. Dans vSphere Client, clic droit sur le template et choisir « Déployer une machine virtuelle à partir du template ».

2. Suivre l’assistant pour configurer le nom de la machine, l’emplacement de stockage, le réseau, les ressources (CPU, RAM), etc.

3. Une fois le déploiement finalisé, la nouvelle machine virtuelle se base sur le template Windows Server.

4. Au premier démarrage de la nouvelle VM, l'assistant de configuration Windows va se lancer pour finaliser la configuration (création d’un compte administrateur, activation du produit, etc.).

##### Ressources

- CPU : 4 vCPUs car j'utilise la version Expérience de bureau de Windows Server, qui utilise beaucoup de ressources,
- RAM : 8 Go car nous avons environ une quarantaine d'imprimantes. Il y a beaucoup de modèles de marques différentes, donc beaucoup de pilotes. Encore une fois, l'expérience de bureau de Windows Server consomme de nombreuses ressources,
- Stockage : 50 Go car peu importe la version, Windows Server est très lourd.

#### Installation du rôle serveur d'impression

L'installation du rôle d'impression se fait très facilement sur Windows Server : 

1. Ouvrir le Gestionnaire de serveur
	1. Se connecter au serveur Windows avec un compte ayant des droits d'administrateur.
	2. Ouvrez le **Gestionnaire de serveur**. 

2. Ajouter le rôle de serveur d'impression
	1. Dans le Gestionnaire de serveur, cliquer sur **Ajouter des rôles et des fonctionnalités**.
	2. Dans l'Assistant, cliquer sur **Suivant** jusqu'à atteindre la page **Sélection du type d'installation**.
	3. Choisir **Installation basée sur un rôle ou une fonctionnalité** et cliquer sur **Suivant**.

3. Sélectionner le serveur
	Sélectionner le serveur sur lequel installer le rôle (généralement, c'est le serveur local) et cliquer sur **Suivant**.

4. Sélectionner le rôle
	1. Dans la liste des rôles, rechercher et cochez **Serveur d'impression**.
	2. Une pop-up peut apparaître pour informer des fonctionnalités supplémentaires qui seront installées. Cliquer sur **Ajouter des fonctionnalités** si nécessaire.
	3. Cliquer sur **Suivant**.

5. Installer les fonctionnalités
	Dans notre cas, aucune fonctionnalité supplémentaire n'est nécessaire, il suffit de cliquer sur **Suivant**.

6. Confirmation et installation
	1. Cliquer sur **Installer**.
	2. L'installation peut prendre quelques minutes. Une fois terminée, il y aura un message de confirmation.

8. Vérification
	Pour vérifier que le rôle a été installé correctement, ouvrir le menu Windows 

#### Ajouter les imprimantes et leurs pilotes

Avant d'installer une imprimante, il est nécessaire d'installer le pilote correspondant.
J'ai donc listé tous les modèles d'imprimante des sociétés, j'ai ensuite téléchargé tous les drivers sur les sites officiels afin d'avoir la dernière version de chacun.
Après les avoir tous installé, j'ai ouvert **Gestion de l'impression** et dans "serveur local", j'ai ajouté les imprimantes en utilisant leur adresse IP.
J'ai utilisé les paramètres TCP/IP afin de créer un port pour chacune. J'ai enfin imprimé une page de test sur les imprimantes de la société dans laquelle je me trouvais pour être sûr que l'adresse et le pilote sont corrects.

Dès que le prestataire à eu fini d'ouvrir les ports, j'ai pu ajouter les imprimantes sur les ordinateurs des utilisateurs petit à petit.

##### Automatisation avec GPO pour ajouter automatiquement les imprimantes :

- **Ouvrir la console de gestion des stratégies de groupe** sur le contrôleur de domaine.
    
- **Créer ou modifier une GPO** qui s'applique aux utilisateurs de chaque société.
    
- **Configurer les préférences de l’imprimante** :
    
    - Dans la GPO, naviguer vers `Configuration utilisateur` -> `Préférences` -> `Paramètres de contrôle` -> `Imprimantes`.
        
    - Faire un clic droit et choisis `Nouvelle` -> `Imprimante`.
        
    - Configurer l’imprimante réseau correspondant à chaque société en utilisant les paramètres appropriés (par exemple, le chemin réseau de l’imprimante).

J'ai mis en place cette GPO afin de simplifier le processus d'ajout des imprimantes.  Pour les utilisateurs actuels, il faut supprimer toutes leurs imprimantes et appliquer la GPO sur la société, mais pour les nouveaux utilisateurs, une fois qu'ils sont dans l'annuaire AD et placés dans la bonne OU, les imprimantes dont ils auront besoins seront immédiatement installées. Cependant, certains utilisateurs comme le HSE ou les membres de la direction se déplacent dans les sociétés et ont besoins des imprimantes de plusieurs sites, il faut donc ajouter celles-ci manuellement.
### 6. Relations avec les principaux acteurs du projet

Pour réaliser ce projet, j'ai été en contact avec plusieurs personnes : 
- Le tuteur d'alternance : afin de s'assurer du bon déroulement du projet,
- Le prestataire informatique : pour l'ouverture des ports et donc autoriser le partage des imprimantes.

### 7. Synthèse et conclusion

Ce projet m'a permis de consolider mes connaissances en virtualisation et de découvrir la mise en place d'imprimantes dans un réseau, fonctionnalité que je n'avais jamais étudié auparavant.


## <font color="#92d050">Projet 4 : Sauvegarde déconnectée + ProxMox</font>

### 1. Compétences mises en œuvre

J'ai mobilisé plusieurs compétences pour mener à bien ce projet :

- Administrer et sécuriser les infrastructures virtualisées,
- Mettre en production des évolutions de l’infrastructure,
- Participer à l’élaboration et à la mise en œuvre de la politique de sécurité,
- Élaborer et mettre en œuvre la politique de sécurité.

### 2. Cahier des charges / Expression des besoins

L'entreprise avait besoin d'une solution efficace et sécurisée pour sauvegarder ses serveurs, en particulier afin de protéger les données sensibles et garantir une récupération rapide en cas de problème ou de panne système. Ce besoin faisait partie d’une stratégie plus large visant à renforcer la sécurité informatique globale et à se préparer à toute éventualité. Le cahier des charges comportait plusieurs objectifs bien définis :

- Mettre en place une infrastructure de sauvegarde fiable basée sur des bandes LTO (Linear Tape-Open), connues pour leur durabilité et leur capacité de stockage élevée.
- Tester la possibilité de récupérer des fichiers provenant d’un système Windows et les restaurer efficacement sur un environnement Debian.
- Réduire les coûts de stockage et de sauvegarde sur le long terme en utilisant des bandes physiques au lieu de services cloud parfois coûteux.
- Assurer une utilisation simple de la solution, accessible aux techniciens même sans connaissances avancées en sauvegarde.
- Préparer des procédures de sauvegarde régulières et documentées pour faciliter la maintenance et les interventions d’urgence.

Plusieurs raisons ont motivé le lancement de ce projet, principalement liées à la sécurité, à la praticité et à l’efficacité :

- **Sécurité renforcée** : Les bandes LTO, une fois stockées hors ligne, sont protégées contre les cyberattaques comme les ransomwares, qui visent souvent les données accessibles en ligne.
- **Économie de ressources** : Contrairement aux solutions en ligne, l’utilisation de bandes réduit les coûts liés aux abonnements cloud et à la gestion de bande passante.
- **Gestion facilitée** : Une fois le système en place, les sauvegardes peuvent être automatisées et les restaurations réalisées à partir d’un support physique stable.
- **Test de compatibilité inter-systèmes** : Vérifier que des fichiers Windows pouvaient être restaurés correctement sur un système Debian permet d’assurer la flexibilité des procédures de récupération en cas d'incident sur un système particulier.
- **Fiabilité à long terme** : Les bandes magnétiques LTO ont une durée de vie estimée à plusieurs décennies, ce qui est essentiel pour la conservation des données archivées.

### 3. Gestion de projet

Pour mener à bien ce projet, j’ai suivi plusieurs étapes :

- **Planification** : définition des besoins et rédaction du cahier des charges.
- **Étude des solutions** : comparaison des différentes options disponibles.
- **Mise en place** : installation du serveur, configuration de Proxmox et des sauvegardes.
- **Tests** : vérification du bon fonctionnement des machines virtuelles et des sauvegardes.
- **Documentation** : rédaction des procédures pour assurer la pérennité du projet.

### 4. Choix des solutions et critères de sélection

Pour ce projet, j’ai choisi :

- **Proxmox** pour la virtualisation, car il est open source, fiable et offre une bonne gestion des ressources.
- **LTO (Linear Tape-Open)** pour la sauvegarde, car c'est une technologie éprouvée pour la conservation des données sur le long terme.
- **WinSCP** pour l’export initial et planifié des données depuis le serveur Windows vers une **VM Linux** dédiée à la sauvegarde.
- **rsync** pour transférer de manière sûre et incrémentale les données stockées sur la VM Linux vers les cartouches **LTO**.
- **Samba** comme solution de remplacement pour le dépôt continu des fichiers, afin de pallier l’absence de fonction de mirroring dans WinSCP.

Les critères de sélection incluaient :

- La compatibilité avec l’infrastructure existante.
- La facilité de mise en place et de maintenance.
- Le coût par rapport aux solutions concurrentes.
- La performance et la fiabilité.

### 5. Organisation de la mise en œuvre

Voici le déroulement détaillé des différentes étapes que j’ai suivies :

1. **Installation de Proxmox** : J’ai commencé par installer Proxmox, un environnement de virtualisation open-source. Il permet de créer facilement des machines virtuelles pour simuler différentes situations, notamment des environnements Windows et Debian.
2. **Préparation du matériel LTO** : J’ai ensuite mis en place le matériel nécessaire, comme le lecteur de bandes, les bandes LTO vierges, et j’ai installé les logiciels de gestion de sauvegarde compatibles.
3. **Création et configuration des machines virtuelles** : J’ai créé plusieurs machines virtuelles : une sous Windows avec des fichiers à sauvegarder, et une autre sous Debian pour simuler le poste de récupération.
4. **Export des données via WinSCP** : Sur le serveur Windows, j’ai programmé des transferts planifiés avec **WinSCP** vers un répertoire sécurisé de la VM Linux de sauvegarde.
5. **Synchronisation vers les bandes avec rsync** : Sur la VM Linux, un **script rsync** incrémental se charge d’envoyer les nouvelles données vers le robot LTO, tout en conservant l’intégrité et l’historique.
6. **Passage à Samba pour le mirroring** : La fonction de mirroring n’étant pas disponible nativement dans WinSCP, j’ai finalement déployé un partage **Samba** sur la VM Linux. Ainsi, le serveur Windows dépose directement ses fichiers dans le partage réseau, ce qui permet une synchronisation continue et plus fiable, tout en simplifiant la supervision des transferts.
7. **Réalisation des tests** : Plusieurs tests ont été faits pour vérifier que les fichiers sauvegardés sous Windows pouvaient être restaurés sans erreurs sur Debian, en gardant leur intégrité.
8. **Contrôles de fiabilité** : J’ai mis en place des vérifications automatiques et manuelles pour m’assurer que les sauvegardes étaient bien effectuées et que les restaurations fonctionnaient correctement.

### 6. Relations avec les principaux acteurs du projet

- **Moi-même** : J’ai assuré la mise en place technique, la configuration des machines virtuelles, les tests de sauvegarde et la création de la documentation.
- **Mon tuteur** : Il m’a accompagné tout au long du projet pour valider les choix techniques, m’aider à résoudre certains blocages, et vérifier la conformité des résultats.

### 7. Synthèse et conclusion

Au cours du projet, j’ai dû faire face à plusieurs difficultés techniques et organisationnelles :

- **Problèmes de compatibilité** : Certains fichiers sauvegardés depuis Windows avaient des autorisations ou des encodages qui posaient problème lors de la restauration sur Debian.
- **Complexité de la gestion des bandes** : Manipuler les bandes LTO demande une certaine rigueur. Il faut bien les identifier, suivre leur rotation, et stocker correctement les anciennes versions.
- **Temps de restauration parfois long** : Restaurer un fichier depuis une bande est plus lent qu’avec un disque dur ou un stockage cloud, ce qui peut être gênant en cas d’urgence.
- **Apprentissage de Proxmox** : Bien que très puissant, Proxmox demande du temps pour être bien maîtrisé, surtout lorsqu’on débute avec la virtualisation.
- **Documentation technique** : J’ai dû créer une documentation claire pour permettre à d’autres personnes de reprendre facilement les opérations si nécessaire.

Ce projet a été particulièrement formateur et enrichissant pour moi. Il m’a permis d’acquérir de nouvelles compétences et de renforcer celles que j’avais déjà :

- **Maîtrise de Proxmox** : J’ai appris à créer, configurer et utiliser des machines virtuelles dans un environnement de production.
- **Utilisation avancée des bandes LTO** : J’ai compris comment fonctionnent les sauvegardes sur bandes, quels sont leurs avantages, mais aussi les précautions à prendre pour éviter les erreurs.
- **Transfert et récupération de fichiers entre systèmes** : J’ai amélioré mes connaissances sur les systèmes de fichiers Windows et Linux, en apprenant à gérer leurs différences.
- **Mise en œuvre de WinSCP, rsync et Samba** : J’ai mis en place une chaîne de transfert complète, du serveur Windows jusqu’aux cartouches LTO, en choisissant les outils les plus adaptés à chaque étape.
- **Rigueur dans la documentation** : J’ai réalisé l’importance de bien documenter toutes les étapes d’un projet pour en faciliter la reprise ou l’évolution.
- **Autonomie et résolution de problèmes** : J’ai dû apprendre à chercher des solutions par moi-même et à tester différentes approches avant de trouver la plus efficace.

La mise en place d’un serveur Proxmox VE et d’une sauvegarde sur bande LTO, couplée à l’usage de WinSCP, rsync et Samba, a été un projet enrichissant. Il a permis de sécuriser les données de l’entreprise tout en optimisant les ressources informatiques. Malgré quelques défis techniques, les objectifs ont été atteints et la solution mise en place est efficace et évolutive. Ce projet m’a également permis de renforcer mes compétences en infrastructure et en gestion de la sécurité des données, ce qui me sera très utile pour la suite de mon parcours professionnel.

En conclusion, ce projet m’a permis de mieux comprendre l’importance d’un bon système de sauvegarde pour une entreprise, et de me familiariser avec des outils professionnels que je pourrai réutiliser dans d’autres contextes.


## <font color="#92d050">Projet 5 : ESP Québec</font>

### 1. Compétences mises en œuvre

J'ai mobilisé plusieurs compétences dans le cadre de ce projet :
- Mesurer et analyser le niveau de sécurité de l’infrastructure,
- Élaborer et mettre en œuvre une politique de sécurité.

### 2. Cahier des charges / Expression des besoins

Lors de mon année d'études au Québec, l’un de mes cours incluait un projet à mettre en place sur un sujet libre en informatique. J'ai donc décidé de concevoir une solution permettant d'auditer et de tester la sécurité d'un réseau avec un dispositif compact et facilement transportable. Mon objectif était de permettre à un attaquant informatique ou à un auditeur en cybersécurité d'exécuter tous les outils nécessaires à son activité sans être encombré et de manière furtive. J'ai conçu ce projet de manière à garantir une autonomie totale dans l'audit et les tests de sécurité des réseaux, en utilisant un matériel portable et discret, adapté aux interventions sur le terrain.

### 3. Gestion de projet

La réalisation de ce projet m'a demandé une organisation rigoureuse ainsi qu'une capacité de recherche et de réflexion considérable. J'ai sollicité l'aide de mes professeurs pour résoudre certains problèmes liés à l'installation et à la configuration des outils. Mes camarades de classe m'ont également apporté leurs connaissances sur différentes attaques et techniques de pentest. Tout au long du projet, j'ai documenté les logiciels utilisés, les configurations mises en place et les ressources consultées. Pour assurer un suivi efficace de mon avancement, j'ai présenté un P.O.C (Proof of Concept) au Cégep. Il nous a également été demandé de séparer les différentes étapes de la mise en place du projet et d'estimer le temps pour les réaliser.

### 4. Choix des solutions et critères de sélection

Pour répondre aux besoins du projet, j'ai sélectionné les composants et logiciels en fonction de plusieurs critères, notamment la performance, la compatibilité et la facilité d'utilisation. Concernant le matériel, j'ai choisi un Raspberry Pi 4, un nano-ordinateur compact, abordable et suffisamment puissant pour mener à bien mon projet. J'ai ajouté un écran GPIO afin d’accéder directement aux applications sans dépendre d’un contrôle à distance. Pour garantir une autonomie complète, j'ai intégré une batterie externe, évitant ainsi toute dépendance à une prise électrique. J'ai également demandé au Cégep de financer une coque de protection pour sécuriser les composants et faciliter le transport du dispositif.

Sur le plan logiciel, j'ai installé Debian, car l’écran n’était compatible qu’avec une version spécifique de Linux fournie par le vendeur. Pour le contrôle à distance, j’ai configuré VNC, une solution efficace permettant d'afficher un flux vidéo en consommant peu de bande passante. Pour l’audit du réseau, j’ai utilisé Lynis, un outil simple et performant réalisant de nombreux tests de sécurité. Pour les tests de phishing, j'ai combiné Zphisher et PhishMailer afin de maximiser la collecte d’informations sur le réseau cible de manière réaliste et rapide. J'ai également voulu préparer une attaque de Rogue Access Point, un piratage de Wi-fi avec aircrack-ng et airgeddon, une DHCP starvation en utilisant DHCPig ainsi qu'un chiffrement de fichiers ; même si je connais les méthodes et logiciels à utiliser, je n'ai pas pu les tester et les inclure car le temps m'a manqué,.

### 5. Organisation de la mise en œuvre

J'ai structuré le projet en plusieurs étapes pour assurer une progression efficace. J'ai commencé par rechercher et sélectionner les composants les plus adaptés. Ensuite, j'ai sollicité l'aide du Cégep pour financer et commander le matériel nécessaire. En attendant la livraison, j’ai analysé et testé différents logiciels Linux spécialisés en audit et pentest. Une fois les composants reçus, je les ai assemblés et vérifiés leur bon fonctionnement. J'ai ensuite mis en place un réseau fictif composé de deux PC, un serveur, un switch et un routeur pour simuler un environnement réaliste. J’ai réalisé plusieurs attaques et audits, documenté chaque étape et analysé les résultats obtenus. Enfin, j'ai présenté mon projet devant un jury, en me plaçant dans la peau d’un auditeur démontrant les attaques cyber possibles au PDG ou au DSI d’une entreprise.

![[RPI.jpg]]
![[Réseau Screenshot.png]]
![[Réseau PT.png]]

[[Réalisation du projet Reynaud Damien]]
### 6. Relations avec les principaux acteurs du projet

À part quelques indications de mes professeurs, des suggestions de mes collègues et une petite aide financière du Cégep, j'ai été le seul à concevoir et réaliser ce projet de bout en bout.

### 7. Synthèse et conclusion

Grâce à ce projet, j’ai pu appliquer mes connaissances en cybersécurité et en administration système dans un contexte concret. J’ai appris à gérer un projet technique du début à la fin, tout en développant mes compétences en audit et en tests de sécurité. Cette expérience m’a permis d’affiner ma méthodologie, d’améliorer ma capacité à résoudre des problèmes techniques et de renforcer mon autonomie dans la gestion de projet.
