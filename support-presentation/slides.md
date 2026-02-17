---
theme: ./theme
title: "n8n à l'heure de l'IA"
info: |
  Factory Tech Digital 113 - 18 février 2026
  Présentation en ligne sur l'intégration de LLMs dans des workflows n8n.
author: Julien Del Rio
keywords: n8n,IA,LLM,workflows,automatisation,Claude,GPT
aspectRatio: 16/9
canvasWidth: 980
fonts:
  sans: Inter
  mono: Fira Code
lineNumbers: true
colorSchema: light
transition: slide-left
mdc: true
layout: cover
---

# n8n à l'heure de l'IA

## Vos workflows avec et par l'IA

<div class="pt-8">
  <p class="text-lg opacity-80">Factory Tech — Digital 113</p>
  <p class="opacity-60">18 février 2026 • 12h15 - 13h45 • En ligne</p>
</div>

<div class="pt-6 text-sm opacity-70">
  <div><strong>Julien Del Rio</strong> — Consultant IA @ Numih France</div>
</div>

---
layout: center
---

# Programme

<div class="grid grid-cols-2 gap-8 pt-8 text-left">
<div>

### Cas d'usage 1

*Exemples de workflows n8n utilisant l'IA*

- Transcription audio avec Whisper
- Analyse de dépôts GitHub avec GPT5-mini

</div>
<div>

### Cas d'usage 2

*Développement d'un workflow avec Claude*

- 4 approches comparées
- Du prompt naïf au workflow opérationnel

</div>
</div>

---
layout: section
---

# Cas d'usage 1

## Exemples de workflows n8n utilisant l'IA

---

# Transcription audio — OpenAI Whisper

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Problème

Whisper impose une **limite de 25 MB** par fichier.
Les fichiers audio longs (réunions, conférences, podcasts) la dépassent.

### Solution

Utiliser **FileFlows** pour segmenter avant transcription.

</div>
<div>

### Workflow

1. Réception du fichier audio
2. Segmentation en morceaux < 25 MB via FileFlows
3. Transcription de chaque segment via l'API Whisper
4. Consolidation en un texte final

### Cas d'usage

Réunions longues, conférences, podcasts, archivage audio

</div>
</div>

<div class="pt-4 text-sm">

Publié dans les [templates officiels n8n](https://n8n.io/workflows/10870-transcribe-long-audio-files-beyond-25mb-limit-with-fileflows-and-openai-whisper/)

</div>

---
layout: center
class: text-center
---

# Démo — Transcription Whisper

## Aperçu du workflow dans l'éditeur n8n

<!--
NOTES DE DEMO :
- Basculer sur l'éditeur n8n
- Montrer le workflow de transcription
- Expliquer les nœuds et le découpage en segments
-->

---

# Analyse d'un dépôt GitHub avec GPT5-mini

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Contexte

Inspiré d'un projet ayant qualifié **4 094 dépôts open source** automatiquement.

### Workflow simplifié

1. Formulaire n8n → saisie d'une URL GitHub
2. Validation du format de l'URL
3. Récupération des métadonnées via API GitHub
4. Récupération du README
5. Analyse par GPT5-mini (réponse JSON structurée)
6. Affichage du résultat

</div>
<div>

### Informations extraites par le LLM

- **Description** de la finalité du projet (2-3 phrases)
- **Catégorie** (library, framework, CLI, API, SaaS…)
- **Stack technique** identifiée depuis le README
- **Score qualité** du README (1 à 5)

### Nœuds n8n utilisés

`formTrigger` → `if` → `github` → `httpRequest` → `merge` → `openAi` → `form`

</div>
</div>

---
layout: center
class: text-center
---

# Démo — Analyse GitHub

## Aperçu du workflow dans l'éditeur n8n

<div class="pt-4 opacity-60">

Workflow disponible dans le dépôt de la présentation : `Digital 113 - Analyser une dépôt github.json`

</div>

<!--
NOTES DE DEMO :
- Basculer sur l'éditeur n8n
- Montrer le workflow d'analyse GitHub
- Saisir une URL GitHub dans le formulaire
- Montrer le résultat structuré retourné par GPT5-mini
-->

---

# Points à retenir — Cas d'usage 1

- Les LLMs s'intègrent **nativement** dans n8n (nœud générique AI Agent ou nœuds dédiés comme OpenAI)
- Les **réponses JSON structurées** permettent une exploitation fluide des résultats
- Une simple **clé d'API** suffit pour commencer à expérimenter
- Possibilité de **combiner plusieurs services IA** dans un même workflow

---
layout: section
---

# Cas d'usage 2

## Développement d'un workflow avec Claude

---

# Objectif

Tester **4 approches** pour générer un workflow n8n avec Claude.

Comparer les résultats selon le **niveau de contexte** fourni au LLM.

---

# Test 1 : claude.ai (prompt naïf)

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Configuration

- **Outil :** interface web claude.ai
- **Contexte fourni :** aucun
- **Prompt :** simple description du besoin

### Résultat attendu

- Générique
- Potentiellement obsolète
- Structure approximative

</div>
<div>

</div>
</div>

---

# Test 1 — Prompt

<div class="prompt-box">

Crée-moi un workflow n8n qui analyse des articles de blog. L'utilisateur saisit une URL dans un formulaire, le workflow récupère le contenu de l'article, l'envoie à GPT via OpenAI pour en extraire un résumé, les mots-clés et le ton, puis affiche le résultat.

</div>

---

# Test 2 : Claude Desktop + Context7

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Configuration

- **Outil :** Claude Desktop avec MCP Context7
- **Contexte fourni :** documentation n8n à jour
- **Prompt :** même besoin + accès docs

### Résultat attendu

- Plus précis grâce à la doc
- Meilleure structure
- Nœuds récents

</div>
<div>

</div>
</div>

---

# Test 2 — Prompt

<div class="prompt-box">

Utilise la documentation n8n via Context7 pour créer un workflow n8n qui analyse des articles de blog.

L'utilisateur saisit une URL dans un formulaire, le workflow récupère le contenu de l'article, l'envoie à GPT via OpenAI pour en extraire un résumé, les mots-clés et le ton, puis affiche le résultat.

Génère le JSON du workflow prêt à importer dans n8n.

</div>

---

# Test 3 : Claude Desktop + specs

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Configuration

- **Outil :** Claude Desktop
- **Contexte :** version n8n + specs techniques
- **Prompt :** besoin + contraintes précises

### Ce qu'on fournit au LLM

- Version n8n : **2.7.4**
- Types et versions exacts des nœuds (formTrigger 2.5, httpRequest 4.4, openAi 2.1, form 2.5)
- Modèle LLM cible : **gpt-5-mini**
- Structure JSON attendue du workflow

</div>
<div>

### Résultat attendu

- Fidèle aux spécifications
- Workflow importable directement
- JSON valide et conforme au format n8n

</div>
</div>

---

# Test 3 — Prompt

<div class="prompt-box text-xs">

Crée un workflow n8n au format JSON importable. Voici les spécifications :

**Version n8n :** 2.7.4

**Nœuds à utiliser (avec types et versions exactes) :**
- `n8n-nodes-base.formTrigger` (typeVersion: 2.5) — formulaire avec un champ "URL de l'article" (requis), responseMode: lastNode
- `n8n-nodes-base.httpRequest` (typeVersion: 4.4) — GET sur l'URL saisie pour récupérer le HTML
- `@n8n/n8n-nodes-langchain.openAi` (typeVersion: 2.1) — analyse du contenu avec le modèle `gpt-5-mini`, réponse en JSON structuré (response_format: json_object) contenant : summary (string), keywords (array), tone (string)
- `n8n-nodes-base.form` (typeVersion: 2.5) — page de complétion affichant le résultat

**Connexions :** formTrigger → httpRequest → openAi → form

**Structure JSON attendue :** le workflow exporté doit contenir les propriétés `name`, `nodes`, `connections`, `pinData` et `settings` à la racine. Chaque nœud doit avoir `parameters`, `type`, `typeVersion`, `position`, `id` et `name`.

</div>

---

# Test 4 : Workflow existant + Context7

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Configuration

- **Outil :** Claude Desktop + MCP Context7
- **Contexte :** workflow de référence + doc n8n à jour
- **Prompt :** s'inspirer du workflow source + documenter

### Ce qu'on fournit au LLM

- Le JSON d'un workflow n8n fonctionnel
- Accès à la documentation n8n via Context7
- Consignes de documentation : nœuds renommés, sticky notes (principale jaune + sections blanches)

</div>
<div>

### Résultat attendu

- Cohérent avec les conventions du projet
- Réutilise les patterns existants
- Documenté avec des sticky notes
- Qualité maximale — le meilleur "prompt" est un exemple

</div>
</div>

---

# Test 4 — Prompt

<div class="prompt-box text-xs">

Utilise Context7 pour accéder à la documentation n8n à jour.

Voici un workflow n8n existant qui analyse des dépôts GitHub : `Digital 113 - Analyser une dépot github.json`

En t'inspirant de sa structure, de ses conventions et de son format, crée un workflow similaire mais qui analyse des **articles de blog** au lieu de dépôts GitHub.

Différences :
- Le formulaire demande une URL d'article (pas une URL GitHub)
- Pas de validation GitHub, pas de nœud github — remplacer par un httpRequest qui récupère le HTML de l'article
- GPT extrait : résumé (2-3 phrases), mots-clés, ton de l'article (au lieu de catégorie/stack/qualité README)
- La page de complétion affiche ces nouveaux champs

Conserve le même style : mêmes versions de nœuds, même structure JSON, mêmes patterns (responseMode, merge, etc.).

**Documentation du workflow :**
- Renomme chaque nœud pour décrire clairement sa fonction
- Ajoute une **sticky note principale** (couleur jaune, en haut à gauche) de 100 à 300 mots avec les sections `### How it works` et `### Setup steps`
- Ajoute des **sticky notes de section** (couleur blanche) pour regrouper les étapes logiques du workflow

</div>

---

# Comparaison des approches

| Test | Outil | Contexte | Qualité attendue |
|------|-------|----------|-------------------|
| 1 | claude.ai | Aucun | Faible |
| 2 | Claude Desktop + Context7 | Documentation n8n | Moyenne |
| 3 | Claude Desktop | Version + specs techniques | Bonne |
| 4 | Claude Desktop + Context7 | Workflow existant + doc n8n | Très bonne |

<div class="pt-6">

### Leçon clé

Le **contexte** est le facteur déterminant de la qualité du résultat.
Plus le LLM dispose d'informations précises, plus le workflow généré est exploitable.

</div>

---

# Pour aller plus loin — Claude Code + n8n

Via l'**API n8n** ou le **serveur MCP n8n**, il est possible d'exporter des workflows en local puis de les réimporter.

- Utiliser **Claude Code** pour générer et modifier des workflows en local
- **Versionner** ses workflows dans un dépôt Git
- Automatiser les mises à jour et le déploiement

<div class="pt-4 text-sm opacity-60">

Un peu overkill pour mes usages actuels — mais le potentiel est là.

</div>

---

# Pour aller plus loin — AI Workflow Builder

n8n intègre un **AI Workflow Builder** qui génère des workflows à partir d'une description en langage naturel.

- Décrivez votre besoin en quelques phrases
- n8n génère automatiquement le workflow correspondant
- Ajustez et personnalisez le résultat dans l'éditeur visuel
- **Disponible uniquement sur n8n Cloud** (non testé)

<div class="pt-4 text-sm">

[docs.n8n.io/advanced-ai/ai-workflow-builder](https://docs.n8n.io/advanced-ai/ai-workflow-builder/)

</div>

---

# Points à retenir — Cas d'usage 2

- Le **contexte** fourni au LLM est le facteur déterminant de la qualité du résultat
- Les outils **MCP** (comme Context7) enrichissent les capacités de l'IA avec des données à jour
- Un **workflow existant** est le meilleur "prompt" — l'exemple bat la spécification

---
layout: end
---

# Merci !

## Échanges et retours d'expérience

<div class="pt-4 text-lg">

**Julien Del Rio** — Consultant IA @ Numih France

</div>
