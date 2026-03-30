# Dossier NEXA-CLOUD — Préparation épreuve EC08

> **Mode d'emploi** : Ce document est ta base de travail. Les zones `[À ADAPTER]` sont les seules parties que tu dois compléter avec les informations des annexes le jour J. Tout le reste est prêt à recopier et à mettre en forme.

***

## PARTIE I — NOTE DE CADRAGE

### 1.1 Objectifs stratégiques du projet

Le projet NEXA-CLOUD vise trois grands objectifs stratégiques :[^1]

- **Commercial** : lancer une offre de Cloud Privé Managé compétitive sous 6 mois afin de capter de nouveaux clients et d'éviter la perte de clients stratégiques susceptibles de se tourner vers la concurrence.
- **Technique** : industrialiser et fiabiliser l'infrastructure (IaC, supervision 24/7, respect des SLA) pour garantir un service de qualité professionnelle.
- **Organisationnel** : réussir la fusion des équipes PRO-IT (35 personnes, on-premise, faible maturité cloud) et NET-SOLUTIONS (15 personnes, réseaux/cybersécurité) en une organisation unifiée, performante et dotée d'une gouvernance claire.

### 1.2 Exigences principales du projet

| Dimension | Exigences |
|-----------|-----------|
| Technique | Mise en place de l'IaC, supervision 24/7, mécanismes de SLA, sécurité réseau et cyber, standardisation des déploiements |
| Organisationnelle | Gouvernance claire, RACI défini, processus d'exploitation formalisés, astreintes opérationnelles |
| SLA | Définition réaliste des niveaux de service, outils de mesure et de reporting SLA, procédures d'escalade |
| Sécurité | Politiques de durcissement, cloisonnement réseau, conformité, implication de l'expertise NET-SOLUTIONS |
| Humaine | Fusion culturelle, montée en compétences cloud/IaC, communication interne, accompagnement au changement |

### 1.3 Périmètre du projet

**Inclus dans le projet :**
- Conception et déploiement de l'infrastructure Cloud Privé Managé
- Mise en place de l'IaC (templates, pipelines, automatisation)
- Déploiement de la supervision 24/7
- Définition et implémentation des SLA et catalogue de services
- Fusion organisationnelle des équipes PRO-IT et NET-SOLUTIONS
- Formation et montée en compétences des équipes
- Conduite du changement
- Recrutement stratégique complémentaire
- `[À ADAPTER selon les annexes : services cloud spécifiques inclus]`

**Hors périmètre :**
- Refonte du SI des clients finaux
- Migration des infrastructures clients existantes (hors périmètre de la phase initiale)
- `[À ADAPTER selon les exclusions mentionnées en annexe]`

### 1.4 Contraintes du projet (Triangle Qualité-Coût-Délai)

| Contrainte | Détail |
|------------|--------|
| **Délais** | 6 mois impératifs — jalons fixes : Gouvernance M1, Design M2, Déploiement infra M4, Pilote M5, Mise en prod M6 |
| **Coûts** | Budget global de 850 000 € — inclut infra, licences, formation, recrutement, accompagnement et réserve risques |
| **Périmètre** | Mise en œuvre complète de l'offre Cloud Privé Managé avec supervision 24/7 et SLA garantis |

> **Enjeu du non-respect du calendrier** : perte de clients stratégiques, dégradation de l'image de marque perçue comme peu innovante, tensions financières à court terme.

### 1.5 Méthodologie de gestion de projet

**Méthode retenue : Hybride (séquentiel pour les phases de cadrage/gouvernance + itératif pour le déploiement technique)**

**Justification :**
- Le cadrage, la gouvernance et la définition des SLA nécessitent une approche structurée et séquentielle (livrables clairs, jalons définis, validation formelle).
- Le déploiement de l'infrastructure et de l'IaC bénéficie d'une approche itérative : livraisons progressives, tests rapides, capacité d'ajustement face aux aléas techniques.
- Cette approche hybride est adaptée à la complexité du projet (fusion de deux cultures, 50 personnes, délai serré de 6 mois) tout en garantissant la rigueur nécessaire pour tenir les SLA et le budget.

**Date de démarrage :** `[À COMPLÉTER selon l'annexe ou le sujet]`

### 1.6 Macro-planning (vue synthétique)

| Mois | Phase principale | Activités clés |
|------|-----------------|----------------|
| M1 | **Cadrage et gouvernance** | Note de cadrage, RACI, organisation projet, processus de gouvernance, choix méthodo |
| M1–M2 | **Design technique** | Architecture cible, choix des outils (IaC, supervision), définition SLA, catalogue de services |
| M2–M4 | **Déploiement infrastructure** | Mise en place IaC, automatisation, déploiement supervision 24/7, sécurité |
| M5 | **Phase pilote** | Validation technique, tests SLA, montée en charge, ajustements, formation équipes exploitation |
| M6 | **Mise en production officielle** | Go live, communication externe, passage en mode récurrent, bilan de projet |
| M2–M6 | **Conduite du changement** | En continu : communication, formation, accompagnement (transversal à toutes les phases) |

### 1.7 Gouvernance du projet

**Ressources identifiées :**

| Profil | Entité d'origine | Rôle dans le projet |
|--------|-----------------|---------------------|
| Chef de projet SI | `[À ADAPTER]` | Pilotage global, coordination, reporting direction |
| Responsable technique Cloud | PRO-IT / NET-SOLUTIONS | Conception et déploiement architecture |
| Référent IaC | `[À ADAPTER selon annexe]` | Mise en place templates, pipelines |
| Référent Supervision / NOC | NET-SOLUTIONS | Supervision 24/7, alerting |
| Référent Sécurité | NET-SOLUTIONS | Politiques cyber, conformité |
| RH / Accompagnement changement | `[À ADAPTER]` | Conduite du changement, formation, recrutement |
| Direction générale | NEXA-CLOUD | Sponsoring, arbitrages, validation jalons |

**Matrice RACI :**

| Activité | Direction | Chef de projet | Resp. Tech. PRO-IT | Resp. Tech. NET-SOL | Équipe infra/cloud | Équipe réseau/cyber | RH |
|----------|-----------|---------------|-------------------|---------------------|--------------------|--------------------|----|
| Validation note de cadrage | A | R | C | C | I | I | I |
| Définition architecture cible | I | R | C | C | R | C | I |
| Choix outils IaC / supervision | I | R | C | C | R | C | I |
| Définition SLA & catalogue services | A | R | C | C | C | C | I |
| Mise en œuvre IaC | I | C | C | C | R | I | I |
| Mise en place supervision 24/7 | I | C | I | C | C | R | I |
| Gouvernance & processus exploitation | A | R | C | C | C | C | I |
| Plan de communication changement | A | R | C | C | I | I | C |
| Ateliers conduite du changement | I | R | C | C | C | C | I |
| Plan de formation | I | R | C | C | C | C | C |
| Validation besoins recrutement | A | R | C | C | C | C | C |
| Rédaction fiche de poste | I | C | C | C | I | I | R |
| Sélection candidats | I | C | C | C | I | I | R |
| Décision embauche | A | C | C | C | I | I | R |

*R = Responsible (réalise) / A = Accountable (valide) / C = Consulted (consulté) / I = Informed (informé)*

### 1.8 Registre des risques (6 risques maximum)

| ID | Risque | Cause principale | Impact | Probabilité | Criticité | Stratégie | Actions de mitigation |
|----|--------|-----------------|--------|------------|-----------|-----------|----------------------|
| R1 | Non-respect du délai de 6 mois | Complexité sous-estimée, ressources insuffisantes | Perte clients, image dégradée, tensions financières | Moyenne | **Élevée** | Réduction | Phasage strict, jalons de Go/No-Go, renfort externe ponctuel si nécessaire |
| R2 | Échec de la fusion culturelle PRO-IT / NET-SOLUTIONS | Résistances, identités fortes, manque de communication | Conflits, démotivation, fuite de talents, baisse performance | Élevée | **Élevée** | Réduction | Plan de communication dédié, ateliers communs, sponsors dans chaque entité, rituels d'équipe |
| R3 | Supervision 24/7 non opérationnelle à temps | Outil mal choisi/configuré, manque de compétences | Incidents non détectés, SLA non tenus, insatisfaction clients | Moyenne | **Élevée** | Réduction | POC précoce (M2), accompagnement éditeur, formation ciblée, tests de scénarios d'astreinte |
| R4 | Manque de compétences IaC | Faible maturité cloud PRO-IT | Erreurs manuelles, lenteur déploiements, dépendance experts | Élevée | Moyenne | Réduction | Plan de formation IaC, binômage avec experts NET-SOLUTIONS, revues de code |
| R5 | SLA définis irréalistes ou non tenus | Mauvaise estimation capacités, absence d'historique | Pénalités clients, perte de contrats, réputation | Moyenne | **Élevée** | Prévention | Co-construction SLA (technique + direction), tests de charge, indicateurs en phase pilote |
| R6 | Dépassement budgétaire | Aléas techniques, recrutement urgent, licences supplémentaires | Blocage projet, arbitrages douloureux | Faible | Moyenne | Acceptation / Réduction | Suivi budgétaire mensuel, réserve risques dédiée incluse dans le budget de 850 k€ |

**Matrice de criticité (probabilité × impact) :**

```
           │ Impact Faible │ Impact Moyen │ Impact Élevé
-----------│---------------│--------------│--------------
Prob. Élevée│               │ R4           │ R2
Prob. Moyenne│              │ R6           │ R1 / R3 / R5
Prob. Faible│               │              │ R6
```

### 1.9 Budget prévisionnel (postes principaux)

| Poste de coût | Nature | Commentaire |
|--------------|--------|-------------|
| Infrastructure cloud | CAPEX / OPEX | Serveurs, stockage, réseau, hyperviseur |
| Licences logicielles | OPEX | Outils IaC, supervision, ticketing, sécurité |
| Formation des équipes | OPEX | Modules IaC, cloud, ITIL, supervision |
| Recrutement | OPEX | Honoraires cabinet, intégration |
| Accompagnement projet | OPEX | Éventuellement consultant externe, conduite du changement |
| Réserve risques | Provision | Incluse dans le budget global de 850 000 € |
| `[À COMPLÉTER]` | `[Annexe 13]` | Reprendre la répartition détaillée de l'annexe 13 |

> **Budget global : 850 000 €** — La répartition précise figure en annexe 13 du dossier. Ne pas inventer de montants par ligne.

***

## PARTIE II — PLAN PROJET

### 2.1 WBS (Work Breakdown Structure — 3 niveaux max)

```
1. CADRAGE DU PROJET
   1.1 Analyse du contexte et des besoins
       1.1.1 Recueil besoins métier, technique, humain
       1.1.2 Analyse des contraintes et hypothèses
   1.2 Note de cadrage et gouvernance
       1.2.1 Rédaction et validation note de cadrage
       1.2.2 Définition RACI et instances de pilotage

2. CONCEPTION DE LA SOLUTION
   2.1 Architecture Cloud Privé Managé
       2.1.1 Définition architecture cible
       2.1.2 Choix des outils (IaC, supervision, sécurité)
   2.2 SLA et catalogue de services
       2.2.1 Définition niveaux de service
       2.2.2 Processus d'exploitation et d'escalade

3. DÉPLOIEMENT INFRASTRUCTURE
   3.1 Mise en place IaC
       3.1.1 Templates et pipelines d'automatisation
       3.1.2 Tests et validation des déploiements automatisés
   3.2 Supervision 24/7
       3.2.1 Déploiement et configuration outil de supervision
       3.2.2 Procédures d'astreinte et d'escalade
   3.3 Sécurité et conformité
       3.3.1 Politiques de durcissement
       3.3.2 Tests de sécurité

4. TESTS ET MISE EN PRODUCTION
   4.1 Phase pilote
       4.1.1 Tests fonctionnels et de charge
       4.1.2 Validation SLA et supervision
   4.2 Mise en production
       4.2.1 Go-live et communication externe
       4.2.2 Bilan de projet et passage en mode récurrent

5. CONDUITE DU CHANGEMENT (transversal)
   5.1 Communication et accompagnement
       5.1.1 Plan de communication interne
       5.1.2 Ateliers et supports pédagogiques

6. DÉVELOPPEMENT DES COMPÉTENCES (transversal)
   6.1 Formation et montée en compétences
       6.1.1 Plan de formation IaC et cloud
       6.1.2 Évaluation et certification
```

### 2.2 Planning Gantt (représentation textuelle)

> **À recopier sous forme de tableau dans ta copie ou sur papier millimétré.**

| Phase / Activité | M1 | M2 | M3 | M4 | M5 | M6 |
|-----------------|----|----|----|----|----|----|
| **1. Cadrage & gouvernance** | ████ | | | | | |
| **2. Design technique** | ▒▒ | ████ | | | | |
| **3. Déploiement infra (IaC, supervision, sécurité)** | | ▒▒ | ████ | ████ | | |
| **4. Phase pilote** | | | | | ████ | |
| **5. Mise en production** | | | | | | ████ |
| **Conduite du changement** | ▒▒ | ████ | ████ | ████ | ████ | ████ |
| **Développement compétences** | ▒▒ | ████ | ████ | ████ | ▒▒ | |
| **Recrutement** | | | ▒▒ | ████ | ▒▒ | |

*████ = phase active / ▒▒ = phase de préparation ou de transition*

**Jalons clés :**
- J1 : Fin cadrage et gouvernance → fin M1
- J2 : Validation architecture et choix outils → fin M2
- J3 : Déploiement infra complet → fin M4
- J4 : Go/No-Go pilote → fin M5
- J5 : Mise en production officielle → fin M6

### 2.3 Dispositif de suivi budgétaire

| Poste de coût | Budget prévu (€) | Consommé (€) | Reste à engager (€) | Écart (%) |
|--------------|-----------------|-------------|---------------------|-----------|
| Infrastructure | `[Annexe 13]` | — | — | — |
| Licences | `[Annexe 13]` | — | — | — |
| Formation | `[Annexe 13]` | — | — | — |
| Recrutement | `[Annexe 13]` | — | — | — |
| Accompagnement / conseil | `[Annexe 13]` | — | — | — |
| Réserve risques | `[Annexe 13]` | — | — | — |
| **TOTAL** | **850 000 €** | — | — | — |

**Mécanisme de suivi :** Revue budgétaire mensuelle en comité de pilotage — comparaison prévu vs réel, déclenchement de la réserve risques si dérive > 10% sur un poste.

### 2.4 Tableau de bord de pilotage (3 KPI)

| KPI | Définition | Cible | Fréquence | Responsable | Source de données |
|-----|------------|-------|-----------|-------------|-------------------|
| **% Avancement global** | Tâches WBS réalisées / total tâches × 100 | ≥ planifié à chaque jalon | Mensuelle | Chef de projet | Plan projet |
| **Respect des jalons** | Jalons atteints à la date prévue / total jalons × 100 | 100% | À chaque jalon | Chef de projet | Planning Gantt |
| **Consommation budgétaire** | Budget consommé / Budget prévu × 100 | ≤ 100% (alerte à 85%) | Mensuelle | Chef de projet + Finance | Tableau suivi budget |

### 2.5 Instances de pilotage (3 maximum)

| Instance | Participants | Fréquence | Objectifs | Livrables |
|----------|-------------|-----------|-----------|-----------|
| **Comité stratégique** | Direction générale, Chef de projet, Sponsors | Mensuelle (fin de mois) | Validation des jalons, arbitrages budgétaires et stratégiques, décisions Go/No-Go | Compte-rendu, décisions formalisées |
| **Comité de pilotage** | Chef de projet, Responsables techniques, RH | Bimensuelle | Suivi avancement, suivi budget, gestion des risques, arbitrages opérationnels | Tableau de bord, registre des risques mis à jour |
| **Rituels opérationnels** | Équipes techniques (infra, réseau, IaC, supervision) | Hebdomadaire | Suivi des tâches en cours, levée des blocages, coordination inter-équipes | Compte-rendu hebdo, backlog de tâches mis à jour |

### 2.6 Arbitrage stratégique — Supervision 24/7 : Internaliser ou externaliser ?

**Contexte :** La supervision 24/7 est un service critique pour Nexa Cloud. L'organisation actuelle ne dispose pas de cette capacité opérationnelle.

| Critère | Internalisation | Externalisation |
|---------|----------------|----------------|
| **Coût** | Investissement initial fort (outils, formation, astreintes) | Coût récurrent maîtrisé, sans investissement initial |
| **Compétences internes** | NET-SOLUTIONS apporte une expertise technique réseaux/cyber, mais manque d'expérience NOC 24/7 | Prestataire spécialisé, opérationnel immédiatement |
| **SLA / qualité de service** | Risque de délai avant montée en compétences | Garanties contractuelles immédiates |
| **Risques organisationnels** | Astreintes : contraintes RH, surcharge en période de démarrage | Dépendance prestataire, moindre maîtrise |
| **Délai de mise en œuvre** | Formation + recrutement : 3-4 mois minimum | Opérationnel en quelques semaines |

**Recommandation argumentée :**

Dans le contexte d'un déploiement imposé en 6 mois avec un budget de 850 000 € et une équipe sans expérience NOC 24/7, **une solution hybride est recommandée** :

- **Court terme (M1–M6) :** externaliser la supervision 24/7 à un prestataire spécialisé afin de garantir les SLA dès le lancement et de ne pas faire peser ce risque sur le planning.
- **Moyen terme (post M6) :** internaliser progressivement via formation et recrutement ciblé, en capitalisant sur l'expérience du prestataire.

> Cette solution garantit la tenue des SLA à court terme (enjeu commercial critique) tout en préservant l'autonomie de Nexa Cloud sur le long terme.

***

## PARTIE III — CONDUITE DU CHANGEMENT

### 3.1 Analyse des impacts organisationnels

#### a) Fusion des équipes PRO-IT et NET-SOLUTIONS

| Dimension | Impacts identifiés | Résistances potentielles |
|-----------|-------------------|------------------------|
| **Identité** | Perte d'appartenance à l'entité d'origine, remise en cause des repères | Sentiment de « dissolution », crainte de domination d'une culture sur l'autre |
| **Méthodes de travail** | PRO-IT : culture on-premise, faible IaC → doit adopter de nouveaux outils et réflexes | Résistance à l'apprentissage forcé de l'IaC, sentiment d'incompétence |
| **Hiérarchie / rôles** | Redéfinition des rôles et responsabilités dans la nouvelle organisation | Conflits de légitimité entre anciens managers PRO-IT et NET-SOLUTIONS |
| **Communication** | 2 cultures d'entreprise différentes, risque de silos | Méfiance réciproque, communication difficile au démarrage |

#### b) Évolution vers un modèle Cloud Privé Managé

| Dimension | Impacts |
|-----------|---------|
| **Outils et pratiques** | Passage de pratiques manuelles on-premise à l'IaC (Terraform/Ansible) et à l'automatisation |
| **Processus d'exploitation** | Introduction de processus ITIL-like (gestion des incidents, des changements, des SLA) |
| **Responsabilité** | Les équipes deviennent responsables de services managés externes → plus grande rigueur requise |
| **Compétences** | Besoin de montée en compétences rapide sur cloud privé, IaC, supervision |

#### c) Introduction de la supervision 24/7

| Dimension | Impacts |
|-----------|---------|
| **Organisation** | Mise en place d'astreintes, rotations, procédures d'escalade |
| **Charge de travail** | Augmentation de la charge perçue, stress potentiel lié aux astreintes |
| **Compétences** | Maîtrise des outils de supervision, compréhension des SLA et des seuils d'alerte |
| **Processus** | Création de runbooks, procédures d'escalade, communication en cas d'incident |

### 3.2 Plan de conduite du changement

#### Communication interne

| Action | Public cible | Message clé | Canal | Fréquence | Porteur |
|--------|-------------|------------|-------|-----------|---------|
| Annonce officielle du projet Nexa Cloud | Toutes les équipes | Vision, objectifs, bénéfices, calendrier | Réunion plénière | Dès M1 | Direction générale |
| Newsletter projet | Toutes les équipes | Avancement, jalons atteints, prochaines étapes | Email / intranet | Mensuelle | Chef de projet |
| Réunions d'équipe | Par entité (PRO-IT / NET-SOLUTIONS) | Impacts spécifiques, réponses aux questions | Réunion présentielle | Bimensuelle | Managers de proximité |
| Communication Go Live | Toutes les équipes + clients | Lancement officiel Nexa Cloud | Email + événement interne | M6 | Direction + chef de projet |

#### Dispositifs d'accompagnement

| Action | Objectif | Public | Période | Format |
|--------|----------|--------|---------|--------|
| Ateliers de cohésion PRO-IT / NET-SOLUTIONS | Créer le lien entre les deux cultures, travailler ensemble | Toutes les équipes | M1–M2 | Workshops mixtes (binômage) |
| Ateliers d'acculturation au cloud privé managé | Comprendre le nouveau modèle et ses enjeux | Équipes techniques | M2–M3 | Formation / démo |
| Accompagnement individuel des managers | Aligner les managers sur la vision, faire redescendre le discours | Managers PRO-IT et NET-SOLUTIONS | M1–M3 | Coaching, échanges |
| Support et FAQ projet | Répondre aux questions, réduire l'anxiété | Toutes les équipes | M1–M6 | Intranet / espace projet |
| Célébration des quick wins | Montrer les bénéfices concrets, maintenir la motivation | Toutes les équipes | Dès M3 | Communication interne, événements |

#### Identification des parties prenantes

| Partie prenante | Impact du changement | Attentes principales | Niveau d'implication requis |
|----------------|---------------------|---------------------|-----------------------------|
| Direction générale | Fort (sponsor, décideur) | ROI, calendrier tenu, image de marque | Très fort (sponsor et décideur) |
| Managers PRO-IT | Fort (changement de modèle, de culture) | Reconnaissance, rôle clair dans la nouvelle organisation | Fort (relais de communication) |
| Managers NET-SOLUTIONS | Moyen (intégration dans une entité plus large) | Valorisation de leur expertise | Fort (référents techniques) |
| Équipes techniques PRO-IT | Fort (montée en compétences cloud, IaC) | Formation, accompagnement, sécurité de l'emploi | Moyen à fort |
| Équipes réseau/cyber NET-SOLUTIONS | Moyen (nouveaux rôles, supervision 24/7) | Valorisation expertise, clarté des astreintes | Moyen |
| Clients Nexa Cloud | Indirect (nouvelle offre, nouveaux SLA) | Fiabilité du service, respect des engagements | Informés (communication externe) |

***

## PARTIE IV — DÉVELOPPEMENT DES COMPÉTENCES

### 4.1 Diagnostic des compétences

| Compétence | Niveau actuel PRO-IT | Niveau actuel NET-SOLUTIONS | Niveau cible Nexa Cloud |
|-----------|---------------------|-----------------------------|------------------------|
| Infrastructure as Code (IaC) | ⬛ Absent | 🟨 Partiel | 🟩 Maîtrisé |
| Cloud Privé (architecture, déploiement) | 🟨 Faible | 🟨 Partiel | 🟩 Maîtrisé |
| Supervision et monitoring | 🟨 Partiel | 🟩 Bon | 🟩 Maîtrisé |
| Supervision 24/7 / astreintes NOC | ⬛ Absent | 🟨 Partiel | 🟩 Maîtrisé |
| Sécurité réseau et cyber | 🟨 Partiel | 🟩 Bon | 🟩 Maîtrisé |
| Gestion SLA / ITIL | 🟨 Partiel | 🟨 Partiel | 🟩 Maîtrisé |
| Automatisation (CI/CD, pipelines) | ⬛ Absent | 🟨 Partiel | 🟩 Maîtrisé |

*⬛ Absent / 🟨 Partiel / 🟩 Maîtrisé*

> Ces niveaux sont à ajuster selon les informations des annexes — ne pas inventer de niveau si une information précise est disponible.

### 4.2 Plan de formation

| Module de formation | Public cible | Format | Durée | Période | Objectif mesurable |
|--------------------|-------------|--------|-------|---------|-------------------|
| IaC (Terraform / Ansible) | Équipes infra PRO-IT | Formation externe + TP | 3 jours | M2–M3 | Capacité à déployer un environnement complet via IaC |
| Architecture Cloud Privé | Toutes équipes techniques | Formation interne + cas pratiques | 2 jours | M2 | Maîtrise de l'architecture cible Nexa Cloud |
| Supervision 24/7 et outils NOC | Équipes exploitation | Formation outil + simulation d'astreinte | 2 jours | M3–M4 | Traitement autonome d'incidents en contexte supervisé |
| Gestion des SLA et processus ITIL | Managers + référents techniques | Formation ITIL / atelier | 1 jour | M2 | Rédaction et suivi d'un SLA client |
| Sécurité cloud | Équipes réseau + infra | Formation éditeur + atelier | 1 jour | M3 | Application des politiques de durcissement sur l'infra |

### 4.3 Indicateurs de succès de la montée en compétences

| Indicateur | Mode de mesure | Cible |
|-----------|---------------|-------|
| % de collaborateurs formés sur IaC | Suivi des présences et validations | 100% des équipes infra avant M4 |
| Résultat à l'évaluation post-formation | Test théorique + mise en pratique | Score ≥ 70% |
| Capacité à traiter un incident de supervision | Simulation en condition réelle | 100% des astreinteurs validés avant Go Live |
| Satisfaction des participants | Questionnaire post-formation | Note ≥ 4/5 |

***

## PARTIE V — RECRUTEMENT

### 5.1 Fiche de poste — Ingénieur Cloud & Supervision (exemple aligné avec les besoins Nexa Cloud)

***

**ENTREPRISE**

Nexa Cloud est une entreprise née de la fusion de PRO-IT, spécialiste des infrastructures on-premise, et NET-SOLUTIONS, expert en réseaux et cybersécurité. Fort de 50 collaborateurs, Nexa Cloud ambitionne de proposer une offre de Cloud Privé Managé à destination des entreprises, garantissant disponibilité, sécurité et performance. Dans le cadre du lancement de cette offre, Nexa Cloud recrute pour renforcer ses équipes opérationnelles.

***

**INTITULÉ DU POSTE**

Ingénieur Cloud & Supervision — `[À ADAPTER selon le besoin identifié en annexe]`

***

**MISSIONS PRINCIPALES**

- Participer à la conception et au déploiement de l'infrastructure Cloud Privé Managé.
- Mettre en place et maintenir les outils d'Infrastructure as Code (IaC) : templates, pipelines d'automatisation, déploiement continu.
- Assurer la supervision 24/7 de l'infrastructure : monitoring, alerting, gestion des incidents, respect des SLA.
- Contribuer à la rédaction et au maintien des runbooks et procédures d'exploitation.
- Participer aux astreintes opérationnelles selon planning défini.
- Travailler en étroite collaboration avec les équipes réseau, sécurité et les équipes issues de la fusion.
- `[À COMPLÉTER selon les missions spécifiques mentionnées en annexe]`

***

**COMPÉTENCES TECHNIQUES REQUISES**

- Infrastructure as Code : Terraform, Ansible (ou équivalent)
- Cloud Privé : maîtrise d'une solution de virtualisation / cloud (VMware, Proxmox, OpenStack…)
- Supervision et monitoring : `[outil mentionné en annexe]` — Zabbix, Prometheus, Grafana, Nagios…
- Sécurité : connaissance des bonnes pratiques de durcissement, cloisonnement réseau, pare-feux
- Automatisation et scripting : Bash, Python, YAML
- Gestion des incidents et SLA : connaissance des principes ITIL souhaitée
- `[À COMPLÉTER selon les outils mentionnés dans le dossier]`

***

**TYPE DE CONTRAT**

- CDI — Temps plein
- Localisation : `[À COMPLÉTER selon annexe ou contexte]`
- Prise de poste : `[À COMPLÉTER]`
- Rémunération : `[À COMPLÉTER selon annexe ou fourchette donnée dans le dossier]`

***

**SOFT SKILLS**

- **Esprit collaboratif** : capacité à travailler dans un contexte de fusion d'équipes et de cultures différentes.
- **Adaptabilité** : aptitude à évoluer dans un environnement en construction et en forte transformation.
- **Rigueur et fiabilité** : sens du service, respect des engagements SLA, capacité à gérer les astreintes avec sérénité.
- **Pédagogie et communication** : capacité à partager ses compétences avec des équipes de niveaux variés.
- **Curiosité technologique** : veille active, goût pour l'amélioration continue.

***

**MODALITÉS D'ÉVALUATION DES CANDIDATS**

| Étape | Format | Objectif | Adaptabilité handicap |
|-------|--------|----------|----------------------|
| Screening CV | Analyse écrite | Vérifier l'adéquation profil / poste | S/O |
| Test technique écrit | QCM / exercice pratique (IaC, supervision) | Évaluer les compétences techniques | Temps majoré, format adapté si nécessaire |
| Entretien technique | Mise en situation (incident, déploiement) | Valider les réflexes opérationnels | Modalités adaptées sur demande |
| Entretien RH | Questions comportementales (STAR) | Évaluer les soft skills et la motivation | S/O |

> La fiche de poste et les modalités de sélection respectent le principe d'égalité des chances et de non-discrimination. Les évaluations sont adaptables en cas de situation de handicap.

***

## MÉMO ORAL (10 min de présentation)

### Structure recommandée (8 slides max)

| Slide | Contenu | Durée approx. |
|-------|---------|---------------|
| 1 | Contexte Nexa Cloud — enjeux de la fusion et du projet | 1 min |
| 2 | Note de cadrage — objectifs, périmètre, contraintes (triangle projet) | 1 min 30 |
| 3 | Risques majeurs (matrice simplifiée) | 1 min |
| 4 | Plan projet — WBS + Gantt (vue synthétique) | 1 min 30 |
| 5 | Budget + KPI + instances de pilotage | 1 min |
| 6 | Conduite du changement — impacts et plan d'accompagnement | 1 min 30 |
| 7 | Développement des compétences + recrutement | 1 min |
| 8 | Synthèse — facteurs clés de succès + recommandation supervision | 30 s |

### Questions probables à anticiper (20 min de questions)

- Pourquoi avoir choisi une méthode hybride plutôt qu'agile ou cycle en V ?
- Comment gérer concrètement le choc culturel entre PRO-IT et NET-SOLUTIONS ?
- Pourquoi externaliser (ou internaliser) la supervision 24/7 ?
- Comment garantir que les SLA seront tenus dès le Go Live ?
- Que faites-vous si le budget est dépassé en M4 ?
- Comment prouver que la montée en compétences sera effective avant le déploiement ?
- Quel est le profil idéal pour le recrutement prioritaire dans votre contexte ?
- Comment vous assurez-vous que les décisions Go/No-Go sont prises au bon niveau ?

---

- **Partie I — Note de cadrage** : objectifs, périmètre, contraintes (triangle projet), méthodo justifiée, macro-planning sur 6 mois avec les jalons officiels, RACI complet, matrice des 6 risques max avec cases de criticité, postes budgétaires.
- **Partie II — Plan projet** : WBS en 3 niveaux, Gantt textuel aligné sur les jalons imposés (M1 → M6), suivi budgétaire mensuel, 3 KPI uniquement, 3 instances de pilotage, et la section arbitrage supervision 24/7 avec recommandation argumentée.
- **Partie III — Conduite du changement** : tableau d'impacts par dimension (fusion, cloud managé, supervision), résistances identifiées, plan de communication, dispositifs d'accompagnement, matrice des parties prenantes.
- **Partie IV — Compétences** : matrice des niveaux actuels vs cibles, plan de formation avec objectifs mesurables, indicateurs de succès.
- **Partie V — Recrutement** : fiche de poste structurée (Entreprise / Missions / Compétences / Contrat / Soft Skills), modalités d'évaluation avec adaptabilité handicap.
- **Mémo oral** : plan des 8 slides + 8 questions probables à anticiper pour les 20 min de questions.



