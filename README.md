# escape-compat

Manifeste de compatibilité des moteurs d’escape (Codex, Claude Code, OpenCode), relu en ligne par escape
au plus une fois par heure (`manifest.json`, servi par `raw.githubusercontent.com`).

- Format : `{"version", "updatedAt", "compatibility": [{"engine", "escapeRange", "recommendedVersion",
  "recommendedRange", "ranges": [{"range", "status"}]}]}`, statuts `supported`, `graceful`, `unsupported`,
  `broken` ou `unknown`, plages à la façon de T3 Code (`>=`, `<`, `=`, `^`, espaces, `||`).
- Chaque modification augmente `version` : escape ignore un manifeste de version inférieure à celui qu’il connaît.
- Ce fichier **restreint** sans jamais élargir : une version ne tourne que si le manifeste embarqué dans la
  build d’escape la dit `supported`. Ici, on marque une version `broken` ou `unsupported`, on change la version
  recommandée et les messages, sans publier une nouvelle version d’escape.
- Aucune donnée personnelle ni secret.
