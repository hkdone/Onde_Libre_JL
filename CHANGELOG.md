# Journal des modifications (Changelog)

Toutes les évolutions notables du projet **Onde Libre Studio** sont consignées dans ce fichier.

Le format suit les principes de [Keep a Changelog](https://keepachangelog.com/fr/1.1.0/).

## [0.1.0] - 2026-11-24 — Jalon 1 : Cadrage technique & documentation initiale (`C14`)

### Ajouté
- `GEMINI.md` : fichier de mémoire projet persistant (`< 200 lignes`) cadrant la stack, les conventions, le rythme par jalons et les interdits explicites.
- `docs/architecture.md` : architecture 4 couches, périmètre v1 / hors v1, modèle relationnel à 10 tables avec contraintes anti-doublons et pipeline 5 statuts, matrice RLS pour 3 rôles (`production`, `diffusion`, `direction`), stratégie d'intégration externe et matrice des 3 cas d'erreur.
- `docs/note-cadrage-direction.md` : note de cadrage non technique adressée à Camille Vasseur (fondatrice d'Onde Libre Studio).
- `docs/jalon-1-guide-presentation.md` : checklist de conformité et trame de présentation orale pour le Jalon 1 avec le mentor.
- `docs/preuves/README.md` et `docs/preuves/J1-C14-synthese-jalon-1.md` : dispositif de collecte continue des preuves RNCP (`C9`–`C14`) et fiche de preuve du Jalon 1.
- `docs/dossier-rncp-brouillon.md` : trame continue des 4 questions du dossier écrit de certification.
- `README.md` et `.env.example` : vitrine du dépôt et modèle de variables d'environnement séparant variables publiques client et secrets serveur.

### Modifié
- `.gitignore` : ajout des règles d'exclusion préventive pour les secrets (`.env`, `.env.*` sauf `!.env.example`), artefacts de build et fichiers système.
- Adaptation environnement validée avec l'équipe pédagogique : **Google Antigravity + Gemini** (`GEMINI.md`) en substitution de Claude Code et Claude Design.
