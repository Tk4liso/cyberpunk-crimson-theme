# cyberpunk-crimson-vscode-theme
A custom Visual Studio Code theme inspired by Cyberpunk Terminal Theme (also in my repos), featuring deep blacks, crimson accents, and a clean, eye-friendly design for long coding sessions.

<img width="1916" height="716" alt="image" src="https://github.com/user-attachments/assets/32708845-4e9d-4fe1-9677-59a250e7df5a" />

# Cyberpunk Crimson — Tema para VS Code

Tema oscuro cyberpunk con **rojo carmesí como acento** (no como color dominante),
pensado para sesiones largas de programación. Inspirado en la paleta
de [Cyberpunk-Terminal-Theme](https://github.com/Tk4liso/Cyberpunk-Terminal-Theme), 
pero adaptado: menos saturación, más contraste controlado.

## Estructura del proyecto

```
cyberpunk-crimson-theme/
├── package.json                              ← manifiesto de la extensión
├── themes/
│   └── Cyberpunk Crimson-color-theme.json    ← el tema en sí (colores + sintaxis)
├── .vscode/
│   └── launch.json                           ← permite correrlo con F5
└── README.md
```

Esto **es** una extensión de VS Code completa, solo que no está publicada en
el Marketplace — vive como carpeta local. VS Code no distingue entre una
extensión "de verdad" y una carpeta local con esta estructura.

## Cómo probarlo (recomendado: F5)

1. Abrir la carpeta `cyberpunk-crimson-theme` completa en VS Code.
2. Presionar **F5** (o `Ejecutar → Iniciar depuración`).
3. Se abrirá una **segunda ventana de VS Code** — el "Extension Development
   Host" — con el tema ya cargado y disponible.
4. En esa segunda ventana: `Ctrl+K Ctrl+T` → seleccionar **Cyberpunk Crimson**.
5. Abrir cualquier archivo en esa ventana para ver el resaltado.


## Cómo instalarlo de forma permanente (sin Marketplace)

Si después de probarlo te gusta y lo quieres usar como tema por defecto,
sin pasar por el modo desarrollo cada vez:

1. Ubica tu carpeta de extensiones:
   - Windows: `%USERPROFILE%\.vscode\extensions`
   - macOS/Linux: `~/.vscode/extensions`
2. Copia **toda la carpeta** `cyberpunk-crimson-theme` dentro de esa ruta.
3. Reinicia VS Code por completo.
4. `Ctrl+K Ctrl+T` → **Cyberpunk Crimson**.

(Alternativa más "prolija": empaquetarlo con `vsce package`, lo que genera
un `.vsix` instalable con `Extensions: Install from VSIX...`. Requiere
`npm install -g @vscode/vsce` — opcional, no es necesario para uso personal.)

## Explicación de las secciones del tema

El archivo `themes/Cyberpunk Crimson-color-theme.json` tiene tres bloques:

### 1. `colors` — la interfaz de VS Code
Controla todo lo que **no** es código: sidebar, activity bar, pestañas,
status bar, terminal integrada, git, minimapa, scrollbars, breadcrumbs,
inputs, notificaciones, etc. Está organizado por secciones con comentarios
(`// ===== NOMBRE =====`) para que sea fácil ubicar qué tocar.

Puntos clave:

- **Fondo**: `#0A0A0A` en editor, sidebar y demás paneles usan variaciones
  muy cercanas (`#0A0A0A`–`#161616`) para dar profundidad sin salirse del
  "negro casi puro".
- **Selección de texto** (`editor.selectionBackground`): rojo carmesí al
  ~28% de opacidad (`#FF3B4C47`), **no** blanco sólido. El texto seleccionado
  se sigue leyendo perfectamente porque es translúcido, no un bloque opaco.
- **Bracket Pair Colorization**: 6 niveles con colores distintos entre sí
  (rojo, cian, amarillo, rosa, verde, naranja) para que aniden sin confundirse.
- **Terminal integrada**: usa los valores ANSI **exactos** del esquema
  "Cyberpunk" del repo de referencia (rojo `#FF1100`, verde `#01A252`,
  amarillo `#FDED02`, etc.), así que al abrir la terminal dentro de VS Code
  se ve prácticamente igual a tu PowerShell.

### 2. `tokenColors` — resaltado de sintaxis clásico (TextMate)

| Elemento       | Color                  |
|----------------|-------------------------|
| Keywords       | Rojo `#FF5566`          |
| Funciones      | Cian `#4FD6E8`          |
| Clases         | Amarillo `#F4D35E`      |
| Strings        | Verde suave `#9CCC65`   |
| Números        | Naranja `#E8935A`       |
| Comentarios    | Gris azulado `#6A7A8C`  |
| Decoradores    | Rosa `#FF6FA5`          |
| Variables      | Gris claro `#C8C8C8`    |

Matices donde mejora la legibilidad sin romper el esquema:
- Parámetros de función: gris claro pero en cursiva y ligeramente más frío
  (`#B8C4D0`) para distinguirlos de variables normales de un vistazo.
- `self`, `True`, `False`, `None`: un rojo-rosado suave (`#FF7A8A`),
  distinto del rojo de keywords, para que no se confundan con `if`/`def`/etc.

### 3. `semanticTokenColors` — resaltado semántico
Cuando Pylance (o el servidor de lenguaje que sea) está activo, VS Code
puede colorear basándose en el significado real del código (no solo en
patrones de texto). Repliqué la misma paleta acá para que sea consistente
sin importar si el resaltado viene del modo "clásico" o del "semántico".

## Cómo modificarlo después

Todo vive en un solo archivo: `themes/Cyberpunk Crimson-color-theme.json`.
No hace falta tocar nada más.

## Sugerencias extra

Esto se logra modificando el settings.json de VS Code:

"editor.cursorBlinking": "phase",

"editor.cursorSmoothCaretAnimation": "on"

Le da al cursor un parpadeo más suave/orgánico en vez del típico parpadeo 
cuadrado. Se siente un poco más "vivo", en línea con la estética.

Para añadir una imagen de fondo instala la extensión Background de Shalldie. Luego en el JSON de preferencias agregar el siguiente código:

```
"background.enabled": true,
    "background.useDefault": false,

    "background.editor": {
        "images": [
            "file:///C:<PATH>/cyberpunk-crimson-theme/background/blade-runner-girl-background.png"
        ],
        "style": {
            "opacity": 0.25,
            "background-position": "right center",
            "background-size": "cover"
        }
    }
```

## Créditos

Paleta de terminal basada en:
[Tk4liso/Cyberpunk-Terminal-Theme](https://github.com/Tk4liso/Cyberpunk-Terminal-Theme).
Este tema de VS Code es una adaptación independiente para uso en editor,
no una copia directa.
