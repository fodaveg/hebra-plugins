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
      "issues": "https://github.com/owner/repo/issues",
      "signingKey": "RWQ…"
    }
  ]
}
```

- Sin versiones ni hashes: la versión sale de la release más reciente del `repo` que traiga
  `hebra.json`, `hebra-main.mjs` y, si hace falta, `hebra-styles.css`.
- `signingKey`: la clave pública minisign con la que el autor firma cada release (la línea
  base64 de su `minisign.pub`, la que empieza por `RW`). Cada release publica, al lado de
  `hebra.json`, su firma `hebra.json.minisig`; Hebra no instala ni actualiza una versión sin
  firma válida con esta clave, ni un plugin que no la tenga aquí. Lo ya instalado sigue
  funcionando. La clave privada no va nunca a GitHub. Para rotarla: PR con la clave nueva;
  las releases firmadas con la vieja dejan de instalarse hasta que se vuelvan a firmar.
  Detalle en `docs/SPEC-PLUGINS-EXTERNOS.md` §8.2.1 de `fodaveg/hebra`, y el script del
  autor es `scripts/firmar-release-plugin.mjs` de ese repo.
- `icon` es un nombre de icono Lucide.
- `id`: minúsculas, números y guiones, de 2 a 64 caracteres. `platforms`: al menos una de las seis del ejemplo.
- El `id` tiene que coincidir con el de `hebra.json` del plugin.

## Alta

Un plugin entra en el listado por pull request a este repo, y lo revisa David. Un plugin
que no esté aquí se puede instalar igualmente desde Ajustes › Plugins › Añadir por URL de
GitHub, marcado como «No está en el listado de Hebra».
