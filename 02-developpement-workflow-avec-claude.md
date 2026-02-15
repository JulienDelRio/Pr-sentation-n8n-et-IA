# Cas d'usage 2 : Développement d'un workflow avec Claude

## Objectif

Tester différentes approches pour générer un workflow n8n avec Claude, en comparant les résultats selon le niveau de contexte et d'outillage fourni.

## Tests

### Test 1 : Interface web de Claude

Demander directement à Claude via [claude.ai](https://claude.ai) de générer un workflow n8n.

- **Contexte fourni :** aucun, prompt simple
- **Attendu :** résultat générique, potentiellement obsolète ou incomplet

<!-- TODO: noter le prompt utilisé et le résultat -->

### Test 2 : Claude Desktop avec MCP Context7

Utiliser Claude Desktop avec le serveur MCP [Context7](https://github.com/upstash/context7) pour donner accès à la documentation n8n à jour.

- **Contexte fourni :** documentation n8n via Context7
- **Attendu :** résultat plus précis grâce à la documentation à jour

<!-- TODO: noter le prompt utilisé et le résultat -->

### Test 3 : Claude Code avec version et détails techniques

Utiliser Claude Code en précisant la version de n8n et des détails techniques spécifiques (format JSON attendu, nœuds disponibles, etc.).

- **Contexte fourni :** version n8n, spécifications techniques, contraintes précises
- **Attendu :** résultat fidèle aux spécifications, workflow importable

<!-- TODO: noter le prompt utilisé et le résultat -->

### Test 4 : Partir d'un workflow existant

Fournir un workflow n8n existant comme base et demander à Claude de le modifier ou de s'en inspirer pour en créer un nouveau.

- **Contexte fourni :** workflow de référence + instructions de modification
- **Attendu :** résultat cohérent avec les conventions du workflow source

<!-- TODO: noter le prompt utilisé et le résultat -->

## Comparaison

| Test | Outil | Contexte | Qualité attendue |
|------|-------|----------|------------------|
| 1 | claude.ai | Aucun | Faible |
| 2 | Claude Desktop + Context7 | Documentation n8n | Moyenne |
| 3 | Claude Code | Version + specs techniques | Bonne |
| 4 | Claude Code | Workflow existant | Très bonne |

## Démonstration

<!-- TODO: notes pour la démo -->
