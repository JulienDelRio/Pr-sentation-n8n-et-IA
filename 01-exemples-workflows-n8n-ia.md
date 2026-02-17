# Cas d'usage 1 : Exemples de workflows n8n utilisant l'IA

## Objectif

Montrer comment intégrer des LLMs (GPT5-mini, Claude, etc.) dans des workflows n8n pour automatiser des tâches intelligentes.

## Exemples de workflows

### Transcription de fichiers audio longs avec OpenAI Whisper

**Template :** [Transcribe long audio files beyond 25MB limit with FileFlows and OpenAI Whisper](https://n8n.io/workflows/10870-transcribe-long-audio-files-beyond-25mb-limit-with-fileflows-and-openai-whisper/)

Contourne la limite de 25 MB d'OpenAI Whisper en utilisant [FileFlows](https://fileflows.com/) pour segmenter les fichiers audio volumineux avant transcription.

**Étapes du workflow :**

1. Réception du fichier audio
2. Segmentation en morceaux < 25 MB via FileFlows
3. Transcription de chaque segment via l'API OpenAI Whisper
4. Consolidation des transcriptions en un texte final

**Cas d'usage :** réunions longues, conférences, podcasts, archivage audio

### Analyse automatique d'un dépôt GitHub avec GPT5-mini

**Article de référence :** [J'ai joué avec ChatGPT : construire une liste projets open source avec n8n, ChatGPT et Google Sheets](https://juliendelrio.fr/2025/02/20/jai-joue-avec-chatgpt-4-construire-une-liste-projets-open-source-avec-n8n-chatgpt-et-google-sheets/)

**Workflow :** [`Digital 113 - Analyser une dépot github.json`](workflows/Digital%20113%20-%20Analyser%20une%20dépot%20github.json)

Inspiré d'un projet ayant permis de qualifier **5 200 dépôts open source** automatiquement, ce workflow simplifié analyse un dépôt GitHub donné via un formulaire et en extrait des informations structurées grâce à GPT5-mini.

**Étapes du workflow :**

1. Saisie de l'URL du dépôt via un formulaire n8n
2. Validation de l'URL (format GitHub)
3. Récupération des métadonnées du dépôt via l'API GitHub
4. Récupération du README
5. Envoi des données à GPT5-mini pour analyse (format JSON structuré)
6. Affichage du résultat : propriétaire, description, catégorie, stack technique, qualité du README

**Informations extraites par le LLM :**

- Description de la finalité du projet (2-3 phrases)
- Catégorie (library, framework, CLI tool, API, SaaS, DevOps, etc.)
- Stack technique identifiée depuis le README
- Score de qualité du README (1 à 5)

**Cas d'usage :** veille technologique, curation de projets open source, audit de dépôts

## Démonstration

<!-- TODO: notes pour la démo -->
