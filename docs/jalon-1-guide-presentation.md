# Guide de présentation — Jalon 1 (Revue Mentor)

Ce guide permet de présenter le **Jalon 1 (Étape 1 — `C14`)** en ~5 minutes lors du point d'étape avec ton mentor, et de valider les 3 arbitrages nécessaires avant de lancer le développement Supabase (Étape 2) et les interfaces (Étape 3).

---

## 1. Checklist de conformité Étape 1 (sujet officiel)

- [x] **Configurer l'environnement de travail et la mémoire projet IA** → `GEMINI.md` (59 lignes `< 200`, conventions, interdits, hygiène de session, adaptation validée **Google Antigravity + Gemini**).
- [x] **Traduire le brief de Camille en document d'architecture technique** → `docs/architecture.md` (entités, cardinalités, pipeline 5 statuts, rôles/RLS, intégrations prévues et gestion des 3 erreurs).
- [x] **Définir l'arborescence du projet et les conventions** → `docs/architecture.md` (section 7), `README.md`, `CHANGELOG.md`, `.env.example`, `.gitignore`.
- [x] **Produire une première note de cadrage lisible par une personne non technique** → `docs/note-cadrage-direction.md` (adressée à Camille Vasseur, zéro jargon).
- [x] **Respecter la règle du Jalon 1 sans code** → aucun fichier applicatif dans `src/` ni dépendance installée avant validation.

---

## 2. Trame de prise de parole (5 minutes)

1. **Le problème d'Onde Libre Studio (30 s)**  
   Camille dirige un studio de 11 personnes (7 podcasts originaux + podcasts de marque) avec **3 nouveaux podcasts à la rentrée**. Les outils actuels (planification, contacts invités, publication, sponsors) ne communiquent pas entre eux. On repart d'une page blanche pour livrer une app unique, sécurisée et maintenable en autonomie.
2. **Le cœur du modèle relationnel (`C10`) (1 min)**  
   10 tables prévues dans Supabase, construites autour du pipeline éditorial strict en 5 statuts (`idee` → `invite_confirme` → `enregistre` → `monte` → `publie`). Les doublons d'invités sont supprimés grâce à la table unique `invites` et la table de jonction N:N `episode_invites` (`UNIQUE (episode_id, invite_id)`). Les campagnes sponsors sont reliées aux épisodes diffusés via `episode_sponsors`.
3. **La sécurité par rôles et RLS (`C13`) (1 min)**  
   Trois rôles stricts : `production`, `diffusion`, `direction`. Les restrictions ne reposent jamais uniquement sur l'affichage UI : elles sont verrouillées en base via **Row Level Security (RLS)**. Les données sensibles (coordonnées privées d'invités, montants/périmètres des campagnes sponsors) sont cloisonnées, et toutes les clés secrètes restent côté serveur (`.env.example`, jamais dans le navigateur).
4. **La stratégie d'intégration externe (`C11`, `C12`) (1 min)**  
   Trois pistes identifiées (Flux RSS Apple Podcasts/hébergeur, Spotify Web API, Ausha/MCP). Dans tous les cas, l'appel se fait côté serveur et alimente une table cache `metriques_audience` : l'interface reste rapide et résiliente face aux 3 pannes obligatoires (**service indisponible**, **réponse vide**, **données invalides**).
5. **L'environnement IA & la traçabilité (`C14`) (1 min)**  
   Avec accord pédagogique, le projet est piloté sous **Google Antigravity + Gemini** avec `GEMINI.md` comme mémoire persistante. Les preuves (`docs/preuves/`) et le brouillon du dossier écrit (`docs/dossier-rncp-brouillon.md`) sont tenus à jour dès ce Jalon 1.

---

## 3. Les 3 points à valider avec le mentor avant l'Étape 2 / Étape 3

| Décision à valider | Proposition retenue par défaut | Question à poser au mentor |
|---|---|---|
| **1. Modèle relationnel (`docs/architecture.md`)** | 10 tables dont `episode_invites`, `episode_sponsors` et `metriques_audience` | Ce schéma couvre-t-il toutes les attentes de l'Étape 2 sans sur-complexifier ? |
| **2. Stack applicative pour l'Étape 3** | **Next.js** (routes API serveur intégrées pour appels API/MCP sans exposer les clés) ou **React + Vite + Supabase Edge Functions** | Y a-t-il une préférence pédagogique entre Next.js et Vite + Edge Functions pour héberger la logique serveur ? |
| **3. Service externe de l'Étape 5** | **Flux RSS podcast** (zéro dépendance clé payante, fiable sur vrai flux Apple Podcasts/Ausha) ou **Spotify Web API** | Quel service externe privilégier pour démontrer au mieux C11/C12 en soutenance ? |
