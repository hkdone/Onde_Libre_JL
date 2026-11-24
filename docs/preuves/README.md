# Suivi des Preuves — Certification RNCP 39108 (Bloc 2 : C9–C14)

Ce dossier centralise les **preuves datées et exploitables** (captures d'écran, exports de tests, logs) produites à chaque étape pour alimenter le dossier écrit (≤ 20 pages, **plafonds stricts de visuels ci-dessous**) et la soutenance orale.

## Convention de nommage
`[Jalon/Etape]-[Competence]-[description-courte].[png|md|txt]`  
Exemples : `J1-C14-arborescence-initiale.png`, `E2-C10-schema-supabase.png`, `J3-C13-test-acces-refuse.png`.

---

## Tableau de suivi des preuves & plafonds de visuels

| Étape / Jalon | Compétence | Preuves à archiver dans `docs/preuves/` | Question dossier & Plafond visuels | Statut |
|---|---|---|---|---|
| **Étape 1 / Jalon 1** | **C14** | Fiche `J1-C14-synthese-jalon-1.md` + capture optionnelle de l'arborescence (`GEMINI.md`, `docs/`), extraits de `docs/architecture.md` et `docs/note-cadrage-direction.md` | **Q4** *(2 visuels max au total)* | ✅ Prêt pour revue mentor |
| **Étape 2** | **C10, C13** | Capture du schéma relationnel Supabase (6+ tables et jonctions), preuve des contraintes `UNIQUE`/`CHECK` (test d'insertion invalide rejetée), captures des politiques RLS actives | **Q2** *(3 visuels max)* & **Q3** | ⬜ À faire |
| **Étape 3 / Jalon 2** | **C9** | Captures des maquettes / prototypes (Design System TweakCN + Gemini / Google Antigravity) + écrans livrés (gestion d'épisode + changement de statut, fiche invité + historique, vue pilotage direction) + adaptation visuelle par rôle + vérif contraste WCAG AA | **Q1** *(3 visuels max)* | ⬜ À faire |
| **Étape 4 / Jalon 3** | **C13, C9** | Capture de la connexion par compte + **preuve de test d'accès refusé** (utilisateur `diffusion` tentant d'accéder aux données `direction` / `campagnes_sponsors`) | **Q3** *(4 visuels max au total)* | ⬜ À faire |
| **Étape 5** | **C11, C12** | Schéma du flux application ↔ API/MCP, capture des données rapatriées affichées en UI, **captures des tests des 3 cas d'erreur** (indisponible, réponse vide, données invalides) avec message et repli | **Q3** *(4 visuels max au total)* | ⬜ À faire |
| **Étape 6** | **C14** | Capture de l'historique Git/GitHub + `CHANGELOG.md`, sommaire du guide d'utilisation, extrait d'une procédure de dépannage, preuve du déploiement accessible (sans URL dans le dossier PDF) | **Q4** *(2 visuels max au total)* | ⬜ À faire |
