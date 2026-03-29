## **Plan de Reprise d’Activité (PRA)**

### 1. Objectif du PRA

Garantir la **continuité d’activité** de l’entreprise d’analyse biologique en cas d’incident majeur (panne matérielle, cyberattaque, sinistre), avec un **RTO de 12 heures** et un **RPO de 4 heures**.

### 2. Identification des systèmes critiques

- **Serveur de fichiers** (résultats d’analyse, documents réglementaires).
- **Serveur de base de données** (LIMS – Laboratoire Information Management System).
- **VM vCenter** (gestion des hyperviseurs).
- **Postes utilisateurs** (indispensables à la saisie et consultation des résultats).
- **Firewall / pare-feu et routeur principal**.
- **Serveur AD / DNS / DHCP**.

### 3. Évaluation des impacts

- **Perte de données > 4 h** : analyses erronées, conformité compromise, litiges possibles.
- **Indisponibilité > 12 h** : arrêt complet des activités de laboratoire, perte de confiance clients, non-conformité réglementaire.
- Risques juridiques (RGPD).

### 4. Objectifs de reprise

- **RTO (Recovery Time Objective)** : 12 heures
- **RPO (Recovery Point Objective)** : 4 heures

### 5. Stratégie de reprise d’activité

#### a. Scénarios de sinistres couverts

- Panne matériel serveur / SAN
- Ransomware
- Erreur humaine
- Incendie / inondation / coupure électrique majeure

#### b. Moyens de reprise

- Plateforme VMware avec snapshots réguliers + sauvegardes Veeam.
- Réplication des VMs critiques vers un **site secondaire distant (autre site ou cloud privé)**.
- Manuel PRA automatisé : playbook + orchestration de restauration.
- Accès distant sécurisé (VPN) pour les équipes IT.

#### c. Procédure de reprise

1. **Déclenchement du PRA** par le RSSI ou DSI.
2. **Basculer l’alimentation sur onduleur/groupe** en cas de coupure électrique.
3. **Démarrage en priorité** des VMs critiques dans l’ordre suivant :
    - AD/DNS/DHCP
    - vCenter
    - Base de données
    - Serveur de fichiers
4. **Vérification de l’intégrité** des données restaurées.
5. **Redirection des utilisateurs** vers l’environnement restauré.

### 6. Préconisations d’évolution de l’infrastructure

- **Mise en place d’un PRA automatisé** (Veeam SureBackup, scripting PowerCLI).
- **Externalisation des sauvegardes critiques vers un cloud souverain** (OVHcloud, 3DS Outscale).
- **Virtualisation des postes critiques (VDI)** pour simplifier leur restauration.
- **Séparation physique ou logique du réseau de sauvegarde** pour éviter la contamination (air gap).
- **Stockage redondant (vSAN ou NAS double contrôleur)**.
- **Audit régulier + simulation de crise annuelle** pour tester la robustesse du PRA.
- Mise en œuvre d’un **SIEM + EDR** pour anticiper les incidents de sécurité.