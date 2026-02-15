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

### Génération de contenu

<!-- TODO: décrire un workflow de génération de contenu -->

### Analyse et classification

<!-- TODO: décrire un workflow d'analyse/classification -->

## Démonstration

<!-- TODO: notes pour la démo -->
