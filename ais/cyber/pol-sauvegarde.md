## **Politique de sauvegarde**

**Objectifs** :

- Garantir la disponibilité et l’intégrité des données critiques (fichiers, bases de données, postes).
- Réduire au minimum le temps d’indisponibilité en cas d’incident.
- Assurer la conformité avec les exigences de confidentialité (ex : RGPD).

**Typologie des sauvegardes** :

- **Sauvegarde complète hebdomadaire** (le week-end).
- **Sauvegarde incrémentale toutes les 4 heures** (alignée avec le RPO).
- **Sauvegarde journalière complète de la base de données**.
- Chiffrement des sauvegardes (AES-256).
- Vérification automatique d’intégrité (hash / logs de vérification).

**Moyens techniques** :

- Utilisation d’un **logiciel de sauvegarde compatible VMware** (ex : Veeam Backup & Replication).
- Sauvegarde en **3-2-1** :
    - 3 copies des données.
    - 2 supports différents (NAS + bande ou cloud).
    - 1 copie hors site (cloud chiffré ou stockage distant).

**Durée de rétention** :

- 30 jours pour les sauvegardes quotidiennes.
- 12 mois pour les sauvegardes hebdomadaires.
- 5 ans pour les archives réglementaires (conformité ISO 15189 / RGPD).

**Tests réguliers** :

- 1 test de restauration partielle / semaine.
- 1 test de PRA complet / semestre.