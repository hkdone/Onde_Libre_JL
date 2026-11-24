# Onde Libre Studio — Application de pilotage éditorial & diffusion

Application web tout-en-un conçue pour **Onde Libre Studio** (SAS, Nantes — fondatrice : Camille Vasseur) afin de remplacer l'empilement d'outils isolés avant le lancement de trois nouveaux podcasts à la rentrée.

Projet professionnel réalisé dans le cadre du titre **RNCP 39108 — Product Builder No-Code (Bloc 2 : `C9` à `C14`)**.

## Stack & environnement

> **Adaptation environnement validée** : avec l'accord de l'équipe pédagogique, le développement assisté par IA s'effectue dans **Google Antigravity** avec **Gemini** et la mémoire projet `GEMINI.md` (en substitution de Claude Code et Claude Design), tout en appliquant intégralement les méthodes, standards d'accessibilité et critères RNCP du cursus.

| Couche / Domaine | Choix technique | Rôle dans le projet |
|---|---|---|
| **IDE & Agent IA** | **Google Antigravity + Gemini** (`GEMINI.md`) | Cadrage, génération contrôlée, documentation et revue qualité. |
| **Design & UI** | **TweakCN** + maquettes **Gemini / Google Antigravity** | Tokens centralisés, Design System accessible (**WCAG AA**), écrans par rôle. |
| **Base de données & Auth** | **Supabase** (PostgreSQL + Auth + **RLS**) | Modèle relationnel anti-doublons, comptes et droits verrouillés par rôle en base. |
| **Intégration externe** | **API REST ou connecteur MCP** (RSS Apple Podcasts / Spotify / Ausha) | Rapatriement de données de diffusion/audience côté serveur + gestion de pannes. |
| **Versionnage & Doc** | **GitHub** + **Markdown** | Suivi des migrations SQL (`supabase/migrations/`), changelog et guides d'autonomie. |

## Avancement par étapes & jalons

| Étape | Contenu | Compétences | Statut |
|---|---|---|---|
| **Étape 1 → Jalon 1** | Cadrage technique, mémoire IA, architecture & note direction *(sans code)* | `C14` | ✅ Prêt pour revue mentor |
| **Étape 2** | Modèle de données Supabase, contraintes & politiques RLS (`supabase/migrations/`) | `C10`, `C13` | ⬜ À faire |
| **Étape 3 → Jalon 2** | Design System, maquettes & application web connectée (≥ 3 écrans, pipeline) | `C9` | ⬜ À faire |
| **Étape 4 → Jalon 3** | Authentification par compte, 3 rôles & tests de blocage d'accès RLS | `C13`, `C9` | ⬜ À faire |
| **Étape 5** | Intégration API/MCP active, gestion des 3 cas d'erreur, repli & justification | `C11`, `C12` | ⬜ À faire |
| **Étape 6** | Versionnage final GitHub, mise en production, guides d'usage & dépannage | `C14` | ⬜ À faire |

## Documentation du projet

- [Mémoire projet IA (`GEMINI.md`)](GEMINI.md) — règles persistantes, conventions et interdits du projet (`< 200 lignes`).
- [Architecture technique (`docs/architecture.md`)](docs/architecture.md) — architecture 4 couches, modèle relationnel, matrice RLS, intégration externe et arborescence.
- [Note de cadrage direction (`docs/note-cadrage-direction.md`)](docs/note-cadrage-direction.md) — cadrage non technique destiné à Camille Vasseur.
- [Guide de présentation Jalon 1 (`docs/jalon-1-guide-presentation.md`)](docs/jalon-1-guide-presentation.md) — trame orale 5 minutes et points de validation mentor.
- [Suivi des preuves RNCP (`docs/preuves/README.md`)](docs/preuves/README.md) — registre des captures et preuves par compétence.
- [Brouillon du dossier RNCP (`docs/dossier-rncp-brouillon.md`)](docs/dossier-rncp-brouillon.md) — préparation continue des 4 questions de soutenance.
- [Journal des modifications (`CHANGELOG.md`)](CHANGELOG.md) — historique des versions livrées.

## Sécurité & variables d'environnement

Aucune clé secrète ni variable d'environnement réelle n'est stockée dans le dépôt. Utiliser [le modèle `.env.example`](.env.example) comme base locale (le fichier `.env` est exclu par `.gitignore`). Les clés secrètes (`SUPABASE_SERVICE_ROLE_KEY`, clés d'API externes) restent strictement côté serveur et ne sont jamais exposées au navigateur.
