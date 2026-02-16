# Support de présentation — n8n à l'heure de l'IA

Présentation Slidev pour la Factory Tech de Digital 113 (18 février 2026).

## Démarrage rapide

```bash
cd support-presentation
npm install
npm run dev
```

Le serveur démarre sur `http://localhost:3030`.

## Thème personnalisé

Le thème `./theme` est inspiré de l'identité visuelle de [juliendelrio.fr](https://juliendelrio.fr/).

### Palette de couleurs

| Variable | Couleur | Usage |
|----------|---------|-------|
| `--jdr-primary` | `#358dd6` | Liens, accents, éléments interactifs |
| `--jdr-primary-dark` | `#25498e` | Titres h1, texte fort |
| `--jdr-secondary` | `#576c8e` | Titres h3, texte secondaire |
| `--jdr-text` | `#0f1d38` | Texte principal |
| `--jdr-bg` | `#ffffff` | Fond des slides |
| `--jdr-bg-alt` | `#f0f5fb` | Fond alternatif (blockquotes, code inline) |

### Typographies

- **Sans-serif :** Inter (Google Fonts)
- **Monospace :** Fira Code (Google Fonts)

### Layouts disponibles

| Layout | Description |
|--------|-------------|
| `cover` | Slide de titre avec logo JDR, gradient bleu foncé |
| `default` | Slide de contenu avec footer discret (logo + pagination) |
| `section` | Séparation de section, texte centré sur gradient bleu |
| `center` | Contenu centré verticalement et horizontalement |
| `two-cols` | Deux colonnes avec séparateur vertical |
| `image-right` | Texte à gauche, image à droite (prop `image`) |
| `end` | Slide de fin avec logo, réseaux sociaux et coordonnées |

### Utilisation des layouts

```markdown
---
layout: cover
---
# Titre principal

---
layout: section
---
# Nouvelle section

---
layout: two-cols
---
# Colonne gauche
Contenu à gauche
::right::
# Colonne droite
Contenu à droite

---
layout: end
---
# Merci !
```

## Commandes

| Commande | Description |
|----------|-------------|
| `npm run dev` | Serveur de développement avec hot-reload |
| `npm run build` | Build statique dans `dist/` |
| `npm run export` | Export PDF |

## Déploiement

Le workflow GitHub Actions (`.github/workflows/deploy.yml`) déploie automatiquement sur GitHub Pages à chaque push sur `main` modifiant `support-presentation/`.

## Structure du thème

```
theme/
├── package.json           # Métadonnées du thème Slidev
├── styles/
│   ├── index.ts           # Point d'entrée des styles
│   ├── base.css           # Couleurs, typographie, éléments de base
│   ├── code.css           # Style des blocs de code
│   └── layouts.css        # Styles spécifiques aux layouts (gradients, etc.)
├── layouts/
│   ├── cover.vue          # Slide de couverture
│   ├── default.vue        # Slide standard
│   ├── section.vue        # Séparateur de section
│   ├── center.vue         # Contenu centré
│   ├── two-cols.vue       # Deux colonnes
│   ├── image-right.vue    # Image à droite
│   └── end.vue            # Slide de fin
└── components/            # Composants Vue réutilisables
```
