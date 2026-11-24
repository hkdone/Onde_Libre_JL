# GEMINI.md — Mémoire projet : Onde Libre Studio

## 1. Identité du projet
- **Client** : Onde Libre Studio (SAS, Nantes, 11 collaborateurs — fondatrice : Camille Vasseur).
- **Produit** : Application web tout-en-un de pilotage éditorial, suivi des invités, diffusion et campagnes sponsors (remplace les outils isolés avant le lancement de 3 nouveaux podcasts à la rentrée).
- **Certification** : Titre RNCP 39108 (*Product Builder No-Code*) — **Bloc 2 (`C9` à `C14`)**.

## 2. Sources de référence (lire en priorité)
- `_ressources/SYNTHESE_SUJET.md` — exigences du sujet, entités, rôles, 6 étapes, 3 jalons, règles du dossier écrit.
- `_ressources/SYNTHESE_COURS.md` — méthodes, conventions, ergonomie/accessibilité WCAG AA, grille RNCP `C9`–`C14`.
- `docs/architecture.md` — architecture 4 couches, modèle relationnel, RLS, intégration externe, arborescence.
- `docs/note-cadrage-direction.md` — cadrage non technique pour Camille Vasseur.
- `docs/dossier-rncp-brouillon.md` & `docs/preuves/README.md` — suivi continu de certification et preuves.

## 3. Stack & outils imposés
- **IA & Pilotage** : Claude Code / agent IA + Skills (`.claude/skills/`).
- **Design & Prototypage** : TweakCN (tokens) + Claude Design (Design System, maquettes, handoff bundle).
- **Base de données, Auth & Sécurité** : **Supabase** (PostgreSQL relationnel + Supabase Auth + **Row Level Security / RLS**).
- **Intégration externe** : **API externe ou connecteur MCP** (diffusion/audience : RSS Apple Podcasts, Spotify ou Ausha).
- **Versionnage & Déploiement** : **GitHub** (Git, changelog) + **Markdown** (`docs/`, `README.md`).

## 4. Rythme strict par étapes & jalons
1. **Étape 1 → Jalon 1** *(sans code)* : `GEMINI.md`, `docs/architecture.md`, `docs/note-cadrage-direction.md`.
2. **Étape 2** : Modèle Supabase + contraintes + RLS, **versionnés dans `supabase/migrations/`**.
3. **Étape 3 → Jalon 2** : Design System + maquettes Claude Design + application web connectée (≥ 3 écrans, pipeline statuts).
4. **Étape 4 → Jalon 3** : Authentification par compte + 3 rôles + tests prouvant le blocage d'accès.
5. **Étape 5** : Intégration API/MCP active + gestion des 3 erreurs (indisponible, vide, invalide) + repli + justification écrite.
6. **Étape 6** : GitHub versionné, mise en production, documentation technique + guide d'usage + dépannage.

**Suivi continu** : après chaque étape validée, archiver les captures/logs dans `docs/preuves/` et mettre à jour `docs/dossier-rncp-brouillon.md`.

## 5. Modèle métier & conventions techniques
- **Entités minimales** : `emissions`, `episodes`, `invites`, `episode_invites`, `enregistrements`, `diffusions`, `campagnes_sponsors`, `profiles`, `metriques_audience`.
- **Pipeline éditorial strict (5 statuts)** : `idee` → `invite_confirme` → `enregistre` → `monte` → `publie`.
- **Rôles (matrice par profil uniquement)** : `production`, `diffusion`, `direction`.
- **Nommage** :
  - SQL (tables, colonnes, contraintes) : `snake_case`, noms de tables au pluriel.
  - Documentation & dossiers : `kebab-case.md`.
  - Dates/heures en base : ISO 8601 (`timestamptz` UTC).
  - Endpoints REST : noms au pluriel (`/episodes/{id}`), verbes HTTP stricts (`GET`, `POST`, `PATCH`, `DELETE`), JSON strict.
  - Markdown : un seul `#` par document, hiérarchie `##`/`###`, liens descriptifs.
- **UI & Accessibilité (WCAG AA)** :
  - Contraste ≥ **4.5:1** (texte normal) / ≥ **3:1** (grand texte), base **16 px**, zones cliquables ≥ **24×24 px**, focus clavier visible.
  - **Jamais la couleur seule** pour indiquer un statut (toujours pastille/icône + libellé textuel).
  - Mobile-first, breakpoints explicites, règle 60/30/10, zéro noir/blanc pur en dark mode.

## 6. Interdits explicites
- **Ne jamais coder l'application** avant la validation du Jalon 1.
- **Ne jamais exposer de clé API secrète ou `service_role` dans le navigateur** : tout appel API authentifié ou secret passe côté serveur / Edge Function.
- **Ne jamais se limiter au masquage UI pour la sécurité** : toute règle d'accès doit être appliquée par **RLS dans Supabase**.
- **Ne jamais soumettre de données réelles sensibles** (emails/téléphones réels, secrets, contrats) dans un prompt externe.
- **Ne jamais relire les PDFs de `_ressources/` en bloc** : travailler sur `_ressources/SYNTHESE_COURS.md` et `_ressources/SYNTHESE_SUJET.md` (n'ouvrir un PDF que sur besoin ponctuel précis).
- **Ne jamais inclure d'URL dans le dossier écrit RNCP** (≤ 20 pages tout compris, dépôt PDF à J-5 + 100 % sur `learning.cube.fr`).
- **Ignorer totalement `_Projet d'étude/`** (hors sujet).

## 7. Hygiène de session IA
- **1 session par tâche ou user story** ; éviter les conversations longues (> 40 % de fenêtre → `/compact` orienté, changement de sujet → `/clear`, mauvaise piste → `/rewind`).
- Pour une reprise critique : fiche de passation (Objectif, État, Décisions, Pistes écartées, Prochaine étape).
- Auditer `GEMINI.md` après chaque jalon (*proposer des ajustements sans modifier directement*) pour le maintenir sous **200 lignes**.
