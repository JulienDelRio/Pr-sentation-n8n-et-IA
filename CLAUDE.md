# Projet : n8n à l'heure de l'IA - les workflows intelligents

## Contexte

Support de présentation pour la **Factory Tech de Digital 113** (18 février 2026).
Présentation en ligne sur l'intégration de LLMs (GPT5-mini, Claude) dans des workflows n8n.

**Intervenants :**
- Julien Del Rio - Consultant IA @ Numih France
- Michael Viala - Directeur de projet @ Granit

## Structure du projet

```
Pr-sentation-n8n-et-IA/          # Dépôt Git cloné (sous-dossier avec son propre .git)
├── README.md                     # Description de l'événement et du programme
├── 01-exemples-workflows-n8n-ia.md   # Cas d'usage 1 : exemples de workflows n8n + IA
├── 02-developpement-workflow-avec-claude.md  # Cas d'usage 2 : générer un workflow avec Claude
├── workflows/
│   └── Digital 113 - Analyser une dépot github.json  # Workflow n8n exporté (JSON)
└── LICENSE                       # Apache 2.0
```

## Git

Le working directory est déjà la racine du dépôt Git (`Pr-sentation-n8n-et-IA/`).
Ne pas préfixer les commandes git par `cd` ni par l'option `-C` — elles fonctionnent directement.

## Contenu des fichiers Markdown

- Les documents sont rédigés en **français** avec accents UTF-8
- Les fichiers contiennent des `<!-- TODO: ... -->` à compléter (notes de démo, prompts, résultats)
- Format Markdown standard avec tableaux comparatifs

## Workflow n8n (JSON)

Le fichier `workflows/Digital 113 - Analyser une dépot github.json` est un workflow n8n exporté :

- **Déclencheur :** formulaire n8n (saisie d'une URL GitHub)
- **Validation :** vérification du format de l'URL (startsWith `https://github.com/`)
- **Extraction :** API GitHub (OAuth2) pour les métadonnées du dépôt + README
- **Analyse IA :** GPT5-mini via le nœud `@n8n/n8n-nodes-langchain.openAi` (réponse JSON structurée)
- **Résultat :** page de complétion avec owner, description, catégorie, stack technique, qualité README

### Nœuds n8n utilisés
- `n8n-nodes-base.formTrigger` (v2.5)
- `n8n-nodes-base.if` (v2.3)
- `n8n-nodes-base.set` (v3.4)
- `n8n-nodes-base.github` (v1.1)
- `n8n-nodes-base.httpRequest` (v4.2)
- `n8n-nodes-base.merge` (v3.2)
- `n8n-nodes-base.form` (v2.5)
- `@n8n/n8n-nodes-langchain.openAi` (v2.1)

## Conventions

- **Langue des documents :** français (avec accents)
- **Licence :** Apache 2.0
- **Format des workflows :** JSON n8n standard (exporté via l'interface n8n)
