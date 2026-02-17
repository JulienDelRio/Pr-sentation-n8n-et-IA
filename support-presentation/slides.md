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

<div class="grid grid-cols-2 gap-8 pt-8">
<div>

### Cas d'usage 1
Exemples de workflows n8n utilisant l'IA

- Transcription audio avec Whisper
- Analyse de dépôts GitHub avec GPT5-mini

</div>
<div>

### Cas d'usage 2
Développement d'un workflow avec Claude

- 4 approches comparées
- Du prompt naïf au workflow opérationnel

</div>
</div>

---

# Qu'est-ce que n8n ?

<div class="grid grid-cols-2 gap-8">
<div>

- Plateforme d'automatisation **open source**
- **400+ intégrations** natives (APIs, bases de données, services cloud)
- Interface visuelle **no-code / low-code**
- Self-hosted ou cloud
- Workflows déclenchés par événements, cron, webhooks, formulaires

</div>
<div>

### Pourquoi n8n + IA ?

- Nœuds natifs pour OpenAI, Anthropic, etc.
- Orchestration de chaînes LLM dans des pipelines
- Traitement de données avant/après l'appel IA
- Réponses structurées (JSON) exploitables

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

# Démo 1

## Analyse d'un dépôt GitHub en direct

<div class="pt-4 opacity-60">

Workflow : `Digital 113 - Analyser une dépôt github.json`

</div>

<!--
NOTES DE DEMO :
- Ouvrir n8n et charger le workflow
- Saisir une URL GitHub dans le formulaire
- Montrer le résultat structuré retourné par GPT5-mini
-->

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

### Observations

<!--
NOTES DE DEMO :
- Copier le prompt dans claude.ai
- Observer la structure du JSON généré
- Tenter l'import dans n8n
- Noter les erreurs / incompatibilités
-->

<div class="p-4 bg-gray-100 rounded-lg text-sm opacity-60 italic">

À compléter pendant la démo

</div>

</div>
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

### Observations

<!--
NOTES DE DEMO :
- Même prompt dans Claude Desktop
- Context7 fournit la doc n8n à jour
- Comparer le JSON avec le test 1
- Vérifier les noms de nœuds et versions
-->

<div class="p-4 bg-gray-100 rounded-lg text-sm opacity-60 italic">

À compléter pendant la démo

</div>

</div>
</div>

---

# Test 3 : Claude Code + specs

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Configuration

- **Outil :** Claude Code
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

### Observations

<!--
NOTES DE DEMO :
- Montrer le CLAUDE.md ou les specs fournies
- Lancer Claude Code avec le contexte technique
- Importer le JSON généré dans n8n
- Vérifier que les nœuds, versions et connexions sont corrects
-->

<div class="p-4 bg-gray-100 rounded-lg text-sm opacity-60 italic">

À compléter pendant la démo

</div>

</div>
</div>

---

# Test 4 : Workflow existant + Context7

<div class="grid grid-cols-[1fr_1fr] gap-8">
<div>

### Configuration

- **Outil :** Claude Code + MCP Context7
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

### Observations

<!--
NOTES DE DEMO :
- Fournir le workflow GitHub comme référence
- Context7 donne accès à la doc n8n à jour
- Vérifier les sticky notes générées
- Comparer la structure avec le workflow source
- Le résultat devrait être le plus fidèle des 4 tests
-->

<div class="p-4 bg-gray-100 rounded-lg text-sm opacity-60 italic">

À compléter pendant la démo

</div>

</div>
</div>

---

# Comparaison des approches

| Test | Outil | Contexte | Qualité attendue |
|------|-------|----------|-------------------|
| 1 | claude.ai | Aucun | Faible |
| 2 | Claude Desktop + Context7 | Documentation n8n | Moyenne |
| 3 | Claude Code | Version + specs techniques | Bonne |
| 4 | Claude Code + Context7 | Workflow existant + doc n8n | Très bonne |

<div class="pt-6">

### Leçon clé

Le **contexte** est le facteur déterminant de la qualité du résultat.
Plus le LLM dispose d'informations précises, plus le workflow généré est exploitable.

</div>

---
layout: center
class: text-center
---

# Démo 2

## Génération d'un workflow avec Claude en direct

<div class="pt-4 opacity-60">

4 tests successifs — du prompt naïf au workflow opérationnel

</div>

<!--
NOTES DE DEMO :
- Test 1 : prompt simple sur claude.ai
- Test 2 : même prompt dans Claude Desktop avec Context7
- Test 3 : Claude Code avec version n8n et specs
- Test 4 : Claude Code avec le workflow existant comme référence
- Comparer les JSON générés et tenter l'import dans n8n
-->

---
layout: center
---

# Points clés à retenir

<div class="grid grid-cols-2 gap-8 pt-6">
<div>

### n8n + IA

- Les LLMs s'intègrent nativement dans n8n
- Orchestration de chaînes de traitement intelligentes
- Réponses structurées pour exploitation automatique

</div>
<div>

### Développer avec l'IA

- Le contexte fourni détermine la qualité
- Les outils MCP enrichissent les capacités de l'IA
- Un workflow existant est le meilleur "prompt"

</div>
</div>

---
layout: end
---

# Merci !

## Échanges et retours d'expérience

<div class="pt-4 text-lg">

**Julien Del Rio** — Consultant IA @ Numih France

</div>
