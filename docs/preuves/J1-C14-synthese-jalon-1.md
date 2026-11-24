# Preuve Jalon 1 (`C14`) — Cadrage technique & documentation initiale

- **Date** : 2026-11-24
- **Compétence RNCP visée** : `C14` — Rédiger des guides d'utilisation, documenter l'architecture, les configurations et le suivi des modifications.
- **Environnement validé** : Google Antigravity (IDE) + Gemini (`GEMINI.md`), en substitution pédagogique de Claude Code et Claude Design.

## 1. Livrables produits au Jalon 1 (sans code applicatif)

- `GEMINI.md` : mémoire projet persistante maintenue sous 200 lignes (`< 200`), contenant stack, conventions, rythme strict par jalons et interdits explicites.
- `docs/architecture.md` : architecture 4 couches, périmètre v1/hors v1, modèle relationnel à 10 tables (`C10`), matrice RLS (`C13`), écrans WCAG AA (`C9`), stratégie API/MCP + 3 erreurs (`C11`/`C12`), arborescence cible.
- `docs/note-cadrage-direction.md` : note de cadrage non technique adressée à Camille Vasseur.
- `docs/jalon-1-guide-presentation.md` : support de revue Jalon 1 avec le mentor.
- `README.md`, `CHANGELOG.md`, `.env.example`, `.gitignore` : socle documentaire, journal des modifications et protection préventive des secrets.
- `docs/dossier-rncp-brouillon.md` & `docs/preuves/README.md` : dispositif de préparation continue de la certification.

## 2. Arborescence du dépôt au Jalon 1

```text
Formation Cube/
├── .env.example
├── .gitignore
├── CHANGELOG.md
├── GEMINI.md
├── README.md
└── docs/
    ├── architecture.md
    ├── dossier-rncp-brouillon.md
    ├── jalon-1-guide-presentation.md
    ├── note-cadrage-direction.md
    └── preuves/
        ├── J1-C14-synthese-jalon-1.md
        └── README.md
```

*(Les dossiers `_ressources/` et `_Projet d'étude/` sont exclus du suivi Git via `.gitignore`.)*

## 3. Vérifications de conformité réalisées

- `GEMINI.md` < 200 lignes : **conforme**.
- Aucun code applicatif (`src/`, `package.json`, `supabase/`) créé avant validation du Jalon 1 : **conforme**.
- Aucune clé API ni secret réel présent dans le dépôt : **conforme**.

## 4. Action manuelle recommandée avant soutenance

- Réaliser une capture d'écran de l'explorateur de fichiers dans **Google Antigravity** montrant `GEMINI.md` et `docs/` ouverts, et l'enregistrer sous `docs/preuves/J1-C14-arborescence-antigravity.png` (utilisable dans Q4 si pertinent, dans la limite de 2 visuels max pour Q4).
