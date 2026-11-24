# Brouillon du Dossier Écrit — RNCP 39108 Bloc 2 (Onde Libre Studio)

> **Rappels de conformité impératifs avant export PDF :**
> - **20 pages maximum tout compris** (≈ 15 pages de contenu rédigé + page de garde + instructions + annexe).
> - **Dépôt PDF au plus tard à J-5** avant la soutenance **ET 100 % de complétion sur `learning.cube.fr`** (sinon annulation automatique).
> - **ZÉRO URL** dans le dossier écrit (non consultées par le jury ; les démos ont lieu en direct en soutenance).
> - **Posture professionnelle** : choisir les exemples les plus parlants, justifier les arbitrages et reconnaître honnêtement les limites/écarts.

---

## Question 1 — Conception des interfaces utilisateur (`C9`) — *3 visuels max*

**Attendus du modèle officiel :**
- Maquettes des écrans clés (gestion d'épisode, fiche invité, vue pilotage direction) et passage maquette → interface développée.
- Parcours le plus révélateur : changement de statut d'un épisode (`idée` → `publié`) et repères visuels montrant ce qui avance et ce qui bloque.
- Fiche invité et historique de participation : organisation de l'information.
- Vue de pilotage direction (épisodes en cours, à venir, publiés) et hiérarchie visuelle.
- Adaptation de l'affichage selon le rôle (`production`, `diffusion`, `direction`).
- Effet recherché vs anciens outils dispersés + écarts assumés entre maquettes et écrans livrés.

**Notes d'étape :**
- *Décisions déjà prises au Jalon 1* : conception du Design System et des maquettes via **TweakCN + Gemini dans Google Antigravity** (adaptation validée pédagogiquement en substitution de Claude Design) ; respect des critères d'accessibilité WCAG AA (contraste ≥ 4.5:1, taille 16 px, **jamais la couleur seule** pour les 5 statuts du pipeline : pastille + icône + libellé), organisation selon les principes de Gestalt et divulgation progressive.
- *À compléter à l'Étape 3 (Jalon 2)* : capture maquette/livré, parcours changement de statut, justification des écarts constatés.

---

## Question 2 — Architecture des données et modèle relationnel (`C10`) — *3 visuels max*

**Attendus du modèle officiel :**
- Schéma relationnel et dictionnaire des données (tables `emissions`, `episodes`, `invites`, `enregistrements`, `diffusions`, `campagnes_sponsors`).
- Cardinalités retenues et tables de liaison (`episode_invites`, `episode_sponsors`).
- Clés et contraintes d'intégrité anti-doublons / anti-incohérences.
- Statuts d'épisode : stockage, valeurs autorisées et enchaînement du pipeline.
- Place des données rapatriées par l'intégration externe (`metriques_audience`).
- Écarts entre le modèle prévu au Jalon 1 et l'implémentation finale à l'Étape 2.

**Brouillon amorcé au Jalon 1 :**
- *Pourquoi ce modèle met fin aux doublons* : dans l'ancien outillage d'Onde Libre Studio, un invité était ressaisi entre l'agenda et le suivi de production. Le passage à une table unique `invites` reliée à `episodes` via la table de jonction `episode_invites` (avec contrainte `UNIQUE (episode_id, invite_id)`) garantit une fiche unique par personne et un historique fiable.
- *Verrouillage du pipeline* : la colonne `episodes.statut` est contrainte par une liste fermée (`idee`, `invite_confirme`, `enregistre`, `monte`, `publie`), alignée sur la validation métier.
- *Préparation des données externes* : la table `metriques_audience` rattachée à `diffusions` stocke à la fois les métriques, l'horodatage `synced_at` et l'état de synchronisation (`ok`, `erreur`, `cache`) afin de dissocier l'affichage UI de la disponibilité immédiate de l'API externe.
- *À compléter à l'Étape 2* : captures du schéma Supabase final, contraintes testées, et tableau des écarts éventuels entre `docs/architecture.md` (Jalon 1) et les migrations SQL réellement déployées.

---

## Question 3 — Intégration d'un service externe et sécurisation des données (`C11`, `C12`, `C13`) — *4 visuels max*

**Attendus du modèle officiel :**
- Choix du service externe (API ou MCP) : besoin couvert, options écartées, limites connues.
- Fonctionnement de l'appel : déclenchement, données demandées, traitement et affichage.
- Comportement en cas de service indisponible, réponse vide ou données invalides : message, repli, tests réalisés.
- Apport métier (diffusion & direction) et effet sur les temps de réponse.
- Classification des données sensibles (coordonnées invités, campagnes sponsors, clés API) et niveau de sécurité appliqué.
- Politiques RLS par rôle en base + **test prouvant qu'un utilisateur `diffusion` n'accède pas aux données `direction`**.
- Stockage des clés hors navigateur + règles de traitement et de conservation.

**Brouillon amorcé au Jalon 1 :**
- *Classification posée dès le cadrage* : séparation en 3 niveaux — données internes non sensibles (émissions, statuts d'épisodes), données personnelles sensibles (`invites.email`, `invites.telephone`), données commerciales sensibles (`campagnes_sponsors`) et secrets techniques (clés API / `service_role` exclusivement côté serveur).
- *Architecture de résilience prévue* : appels externes effectués côté serveur + cache en base (`metriques_audience`) pour ne pas pénaliser le temps de chargement des pages et garantir un repli immédiat en cas de panne.
- *À compléter aux Étapes 2, 4 et 5* : justification définitive du service choisi (Flux RSS / Spotify / Ausha), résultats des tests d'erreurs simulées, capture politique RLS + capture du test d'accès refusé `diffusion` → `campagnes_sponsors`.

---

## Question 4 — Documentation et passation de l'outil (`C14`) — *2 visuels max*

**Attendus du modèle officiel :**
- Architecture et configurations documentées : base, sécurité/RLS, intégration, déploiement.
- Instructions d'utilisation par rôle (`production`, `diffusion`, `direction`).
- Procédures de dépannage : intégration en échec, utilisateur sans accès, déploiement qui échoue.
- Enregistrement des modifications : historique du dépôt GitHub, journal des changements (`CHANGELOG.md`).
- Rôle du fichier de mémoire projet (`GEMINI.md`) dans la collaboration avec l'agent IA et pour la reprise du projet.

**Brouillon amorcé au Jalon 1 :**
- *Dès l'Étape 1, la documentation et la reprise sont posées comme fondations* :
  - **Arbitrage d'outillage documenté** : avec l'accord des responsables pédagogiques, l'environnement **Google Antigravity + Gemini** est utilisé en substitution de Claude Code et Claude Design. Cet arbitrage démontre la portabilité des méthodes apprises (cadrage amont, hygiène de contexte, Design System, sécurité RLS).
  - `GEMINI.md` (< 200 lignes à la racine, équivalent natif d'`agent.md` / `CLAUDE.md`) fixe de façon persistante l'architecture, les conventions de nommage, la stack, le rythme par jalons et les interdits explicites (ex. interdiction de contourner la RLS côté UI ou d'exposer des clés côté client), évitant toute dérive de l'agent IA d'une session à l'autre.
  - `docs/architecture.md` formalise les choix techniques (schéma relationnel, matrice de droits, flux API et gestion d'erreurs) pour tout développeur repreneur.
  - `docs/note-cadrage-direction.md` garantit l'alignement avec Camille Vasseur sans jargon technique.
  - `README.md`, `CHANGELOG.md` (`v0.1.0`) et `.env.example` posent dès le Jalon 1 les bases de passation, de traçabilité des versions et d'hygiène des secrets (preuve archivée dans `docs/preuves/J1-C14-synthese-jalon-1.md`).
- *À compléter à l'Étape 6* : guides d'usage par rôle, procédures de dépannage testées, capture de l'historique des commits/migrations et du `CHANGELOG.md` *(sans aucune URL dans le PDF final)*.
