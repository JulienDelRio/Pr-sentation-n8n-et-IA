# Cas d'usage 2 : Développement d'un workflow avec Claude

## Objectif

Tester différentes approches pour générer un workflow n8n avec Claude, en comparant les résultats selon le niveau de contexte et d'outillage fourni.

**Cas commun à tous les tests :** créer un workflow n8n qui analyse des articles de blog (formulaire → récupération HTML → analyse GPT via OpenAI → affichage résultat).

## Tests

### Test 1 : Interface web de Claude

Demander directement à Claude via [claude.ai](https://claude.ai) de générer un workflow n8n.

- **Contexte fourni :** aucun, prompt simple
- **Attendu :** résultat générique, potentiellement obsolète ou incomplet

**Prompt :**

> Crée-moi un workflow n8n qui analyse des articles de blog. L'utilisateur saisit une URL dans un formulaire, le workflow récupère le contenu de l'article, l'envoie à GPT via OpenAI pour en extraire un résumé, les mots-clés et le ton, puis affiche le résultat.

<!-- TODO: noter le résultat -->

### Test 2 : Claude Desktop avec MCP Context7

Utiliser Claude Desktop avec le serveur MCP [Context7](https://github.com/upstash/context7) pour donner accès à la documentation n8n à jour.

- **Contexte fourni :** documentation n8n via Context7
- **Attendu :** résultat plus précis grâce à la documentation à jour

**Prompt :**

> Utilise la documentation n8n via Context7 pour créer un workflow n8n qui analyse des articles de blog.
>
> L'utilisateur saisit une URL dans un formulaire, le workflow récupère le contenu de l'article, l'envoie à GPT via OpenAI pour en extraire un résumé, les mots-clés et le ton, puis affiche le résultat.
>
> Génère le JSON du workflow prêt à importer dans n8n.

<!-- TODO: noter le résultat -->

### Test 3 : Claude Code avec version et détails techniques

Utiliser Claude Code en précisant la version de n8n et des détails techniques spécifiques (format JSON attendu, nœuds disponibles, etc.).

- **Contexte fourni :** version n8n, spécifications techniques, contraintes précises
- **Attendu :** résultat fidèle aux spécifications, workflow importable

**Prompt :**

> Crée un workflow n8n au format JSON importable. Voici les spécifications :
>
> **Version n8n :** 2.7.4
>
> **Nœuds à utiliser (avec types et versions exactes) :**
> - `n8n-nodes-base.formTrigger` (typeVersion: 2.5) — formulaire avec un champ "URL de l'article" (requis), responseMode: lastNode
> - `n8n-nodes-base.httpRequest` (typeVersion: 4.4) — GET sur l'URL saisie pour récupérer le HTML
> - `@n8n/n8n-nodes-langchain.openAi` (typeVersion: 2.1) — analyse du contenu avec le modèle `gpt-4o-mini`, réponse en JSON structuré (response_format: json_object) contenant : summary (string), keywords (array), tone (string)
> - `n8n-nodes-base.form` (typeVersion: 2.5) — page de complétion affichant le résultat
>
> **Connexions :** formTrigger → httpRequest → openAi → form
>
> **Structure JSON attendue :** le workflow exporté doit contenir les propriétés `name`, `nodes`, `connections`, `pinData` et `settings` à la racine. Chaque nœud doit avoir `parameters`, `type`, `typeVersion`, `position`, `id` et `name`.

<!-- TODO: noter le résultat -->

### Test 4 : Partir d'un workflow existant

Fournir un workflow n8n existant comme base et demander à Claude Code (avec Context7) de le modifier ou de s'en inspirer pour en créer un nouveau, en suivant les bonnes pratiques de documentation n8n.

- **Contexte fourni :** workflow de référence + documentation n8n via Context7 + consignes de documentation
- **Attendu :** résultat cohérent avec les conventions du workflow source, documenté avec des sticky notes

**Prompt :**

> Utilise Context7 pour accéder à la documentation n8n à jour.
>
> Voici un workflow n8n existant qui analyse des dépôts GitHub : `Digital 113 - Analyser une dépot github.json`
>
> En t'inspirant de sa structure, de ses conventions et de son format, crée un workflow similaire mais qui analyse des **articles de blog** au lieu de dépôts GitHub.
>
> Différences :
> - Le formulaire demande une URL d'article (pas une URL GitHub)
> - Pas de validation GitHub, pas de nœud github — remplacer par un httpRequest qui récupère le HTML de l'article
> - GPT extrait : résumé (2-3 phrases), mots-clés, ton de l'article (au lieu de catégorie/stack/qualité README)
> - La page de complétion affiche ces nouveaux champs
>
> Conserve le même style : mêmes versions de nœuds, même structure JSON, mêmes patterns (responseMode, merge, etc.).
>
> **Documentation du workflow :**
> - Renomme chaque nœud pour décrire clairement sa fonction
> - Ajoute une **sticky note principale** (couleur jaune, en haut à gauche) de 100 à 300 mots avec les sections `### How it works` et `### Setup steps`
> - Ajoute des **sticky notes de section** (couleur blanche) pour regrouper les étapes logiques du workflow (ex: "Récupération de l'article", "Analyse IA", "Affichage du résultat"). Chaque sticky de section doit contenir un titre court et 1-2 lignes maximum.

<!-- TODO: noter le résultat -->

## Comparaison

| Test | Outil | Contexte | Qualité attendue |
|------|-------|----------|------------------|
| 1 | claude.ai | Aucun | Faible |
| 2 | Claude Desktop + Context7 | Documentation n8n | Moyenne |
| 3 | Claude Code | Version + specs techniques | Bonne |
| 4 | Claude Code | Workflow existant | Très bonne |

## Démonstration

<!-- TODO: notes pour la démo -->
