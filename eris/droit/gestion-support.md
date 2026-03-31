## 1. Rôle du support informatique et vision ITIL 4

- Mission du support : assurer la continuité et la qualité des services numériques pour les utilisateurs en résolvant incidents, traitant les demandes et accompagnant les changements.  
- ITIL 4 : cadre de bonnes pratiques pour la gestion des services IT (ITSM), qui aide à structurer les processus du support autour de la création de valeur pour le métier.  

À ton avis, si tu devais l’expliquer à un manager non technique, comment résumerais‑tu en une phrase ce qu’apporte ITIL 4 au support ?

***

## 2. ITIL 4 en bref (adapté au support)

### 2.1 Concepts clés

- Service : moyen de créer de la valeur pour les clients en leur permettant d’obtenir les résultats qu’ils veulent, sans gérer les coûts/risques associés.  
- Valeur et co‑création : la valeur est co‑créée par le fournisseur IT et le métier (le support a un rôle central dans cette relation).  
- Organisation, personnes, partenaires, processus : base de la vision “système” d’ITIL 4.  


### 2.2 Les 4 dimensions (vu “support”)

- Organisation \& personnes : équipes L1/L2/L3, rôles, compétences, culture de service.  
- Information \& technologie : outils ITSM, base de connaissances, CMDB, monitoring.  
- Partenaires \& fournisseurs : contrats de support éditeurs, infogérants, maintenance matériel.  
- Flux de valeur \& processus : comment une demande circule du contact utilisateur à la résolution.  


### 2.3 Principes directeurs utiles au support

Parmi les 7 principes, ceux qui parlent le plus :

- Se concentrer sur la valeur : prioriser ce qui impacte le métier, pas juste la techno.  
- Commencer où vous êtes : formaliser les pratiques existantes au lieu de tout réinventer.  
- Progresser par itérations avec feedback : petites améliorations sur les workflows, KPI, FAQ.  
- Collaborer et promouvoir la transparence : partage d’infos entre support, infra, dev, métiers.  

***

## 3. Organisation du support : L1 / L2 / L3

### 3.1 Niveaux de support

- L1 (service desk / help desk)  
    - Point d’entrée unique (téléphone, portail, mail, chat).  
    - Enregistre, catégorise, priorise les tickets.  
    - Résout les demandes simples et les incidents standardisés (FCR) ou escalade.  
- L2  
    - Techniciens / ingénieurs spécialisés (poste de travail, réseau, systèmes, applicatifs).  
    - Analyse plus poussée, accès aux consoles d’admin, gestion des incidents complexes.  
- L3  
    - Experts internes (architectes, devs) ou externes (éditeurs, constructeurs).  
    - Corrige les causes profondes (bugs, limitations produits, patchs).  


### 3.2 Rôles clés

- Agent service desk, Owner d’incident, Problem manager, Change authority, etc.  
- Importance de la collaboration entre support et équipes projet / dev.  

***

## 4. Processus ITIL 4 essentiels pour le support

### 4.1 Service Desk

- Pratique qui représente le point de contact unique entre utilisateurs et DSI.  
- Activités : accueil, enregistrement, information, communication, suivi, satisfaction.  


### 4.2 Incident Management

- Objectif : restaurer le service au plus vite (solution définitive ou contournement).  
- Cycle type :  

1. Détection / création du ticket.  
2. Enregistrement, catégorisation, priorisation.  
3. Diagnostic / résolution ou escalade.  
4. Validation utilisateur.  
5. Clôture avec documentation.  


### 4.3 Service Request Management

- Objectif : traiter efficacement les demandes standard (comptes, droits, postes, logiciels).  
- Utilise un catalogue de services, des modèles de demande et souvent de l’automatisation/self‑service.  


### 4.4 Problem Management

- Objectif : identifier et traiter les causes racines des incidents récurrents.  
- Outils : analyses, base d’erreurs connues, liens incident ↔ problème.  


### 4.5 Change Enablement (vu côté support)

- Objectif : introduire des changements dans le SI en maîtrisant risques et impacts.  
- Le support doit : être informé des changements, préparer FAQ, scripts, communication, plan de bascule et de retour arrière.  

***

## 5. Modèle de gestion des tickets

### 5.1 Cycle de vie générique d’un ticket

1. Création  
    - Entrée via portail, mail, téléphone, monitoring.  
2. Enregistrement  
    - Vérification des informations, association à un utilisateur, choix du type (incident/demande).  
3. Catégorisation et priorisation  
    - Catégorie / sous‑catégorie ; impact + urgence → priorité (P1 à P4).  
4. Affectation  
    - Routage vers le bon groupe (L1/L2/L3) ou file générique.  
5. Investigation et résolution  
    - Diagnostic, tests, escalades, documentation des actions.  
6. Validation  
    - Confirmation utilisateur que le service est correct.  
7. Clôture  
    - Renseigner la cause, la solution, lier aux problèmes/changements, archiver.  

### 5.2 Modèle de ticket (champs recommandés)

- Demandeur : identité, service, contact, localisation.  
- Contexte : service/CI impacté, environnement (prod, test, poste local).  
- Description : symptôme, message, date de début, fréquence, actions déjà réalisées.  
- Classification : type (incident / demande), catégorie, sous‑catégorie.  
- Impact / urgence / priorité.  
- SLA associé (temps de réponse, temps de résolution).  
- Journal d’actions (horodaté, lisible par L2/L3 et auditable).  
- Résolution (cause, solution, contournement, document lié).  

***

## 6. Matrice impact / urgence → priorité

### 6.1 Logique

- Impact : étendue des conséquences (utilisateur unique, équipe, service critique, site entier).  
- Urgence : délai acceptable avant que l’impact ne devienne inacceptable.  


### 6.2 Exemple de matrice

| Impact \ Urgence | Haute | Moyenne | Basse |
| :-- | :-- | :-- | :-- |
| Élevé | P1 – Critique | P2 – Majeur | P3 – Significatif |
| Moyen | P2 – Majeur | P3 – Significatif | P4 – Mineur |
| Faible | P3 – Significatif | P4 – Mineur | P4 – Mineur / planifiable |

- P1 : service critique indisponible pour un grand nombre d’utilisateurs.  
- P2 : impact significatif mais contournable ou moins large.  
- P3/P4 : incidents limités ou demandes non urgentes.  

***

## 7. SLA (Service Level Agreements) et indicateurs

### 7.1 Contenu d’un SLA support

- Périmètre : services couverts, types de demandes, publics concernés.  
- Horaires de support (ex : 8h–18h J+S, 24/7 pour P1).  
- Engagements de délai par priorité, par exemple :  
    - P1 : prise en charge 15–30 min, résolution cible 2–4 h.  
    - P2 : prise en charge 1 h, résolution 4–8 h.  
    - P3 : prise en charge 4 h, résolution 2 jours.  
    - P4 : prise en charge 1 jour, résolution 5 jours ouvrés.  
- Règles d’escalade et de communication.  


### 7.2 SLA par type de demande standard

- Création de compte : traitement sous 1 jour ouvré après validation.  
- Déploiement d’un poste standard : sous 5 jours ouvrés après commande.  
- Ajout de droits sur une appli : sous 2 jours après validation manager.  


### 7.3 Indicateurs de pilotage

- Temps moyen de prise en charge, temps moyen de résolution (MTTR).  
- % de tickets résolus dans les délais SLA, par priorité et par service.  
- Taux de résolution au premier contact (FCR).  
- Volume de tickets par période, par catégorie.  
- Satisfaction utilisateur (enquêtes post‑ticket).  

***

## 8. Gestion du parc et support proactif

- Gestion de parc : inventaire matériel/logiciel, cycle de vie des postes, standardisation, contrats.  
- Supervision : détection proactive (disques pleins, services down, latence élevée) → tickets auto.  
- Proactivité : campagnes de patch, automatisation (scripts, GPO, outils de déploiement), FAQ/self‑service, formation utilisateurs.  

***

## 9. Compétences d’un bon gestionnaire de support

- Techniques : systèmes, réseau, sécurité, outils ITSM, scripting, connaissance du SI.  
- Organisationnelles : priorisation, respect des processus ITIL, documentation, gestion du temps.  
- Relationnelles : écoute, vulgarisation, gestion des situations tendues, orientation client.  

