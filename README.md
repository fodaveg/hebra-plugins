# hebra-plugins

Listado de plugins de [Hebra](https://app.hebra.pro). Hebra lo lee desde
`https://raw.githubusercontent.com/fodaveg/hebra-plugins/main/plugins.json` y lo enseña en
Ajustes › Plugins.

## Formato

```json
{
  "schema": 1,
  "plugins": [
    {
      "id": "mi-plugin",
      "name": "Mi plugin",
      "description": "Qué hace, en una frase.",
      "author": "Nombre",
      "repo": "owner/repo",
      "icon": "puzzle",
      "platforms": ["macos", "ios", "linux", "windows", "android", "web"],
      "ageRating": "4+",
      "homepage": "https://…",
      "issues": "https://github.com/owner/repo/issues"
    }
  ]
}
```

- Sin versiones ni hashes: la versión sale de la release más reciente del `repo` que traiga
  `hebra.json`, `hebra-main.mjs` y, si hace falta, `hebra-styles.css`.
- `icon` es un nombre de icono Lucide.
- `id`: minúsculas, números y guiones, de 2 a 64 caracteres. `platforms`: al menos una de las seis del ejemplo.
- El `id` tiene que coincidir con el de `hebra.json` del plugin.

## Alta

Un plugin entra en el listado por pull request a este repo, y lo revisa David. Un plugin
que no esté aquí se puede instalar igualmente desde Ajustes › Plugins › Añadir por URL de
GitHub, marcado como «No está en el listado de Hebra».
