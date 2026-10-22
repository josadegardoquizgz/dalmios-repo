# dalmios-repo

Repositorio de distribución de **DalmiOS**: aquí solo hay lo que los equipos con
DalmiOS descargan, nunca código fuente.

| Archivo | Qué es |
|---|---|
| `index.json` | Los paquetes que ofrece `dalmi` (nombre, versión, URL, SHA-256) |
| `system/manifest.txt` | La última versión de DalmiOS: versión, URL, SHA-256 y tamaño de su imagen de arranque |
| `system/dalmios-X.Y.Z.fat` | Esa imagen de arranque |
| `*.sig` | Firma Ed25519 de cada archivo, hecha con la clave privada de publicación |

DalmiOS lleva dentro la clave pública y **no usa nada que no esté firmado con
la privada**: un índice o una actualización modificados, o publicados por otra
persona, se rechazan. La clave privada no está en ningún repositorio.

En DalmiOS:

```
dalmi update     # descarga el índice y el manifiesto, y comprueba sus firmas
dalmi list       # los paquetes, y si hay una versión nueva del sistema
dalmi upgrade    # actualiza los paquetes y, si la hay, instala la versión nueva
```

Los archivos de este repositorio se generan con `tools/release/dalmios_release.py`
(en el código de DalmiOS); no se editan a mano, porque la firma dejaría de valer.
