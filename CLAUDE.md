# Animalol — proyecto de video (iPartner)

## Requerimiento del usuario: declarar las skills usadas

En **cada** respuesta, indicar al final y entre paréntesis qué skill se usó:

> *(skill usada: `motion-graphics`)*

- Si se usó más de una, listarlas todas.
- Si **no** se usó ninguna, decirlo explícitamente — nunca omitir la línea.

## Marca iPartner

| Color | Hex |
|---|---|
| Casi negro violáceo | `#17122b` |
| Índigo | PENDIENTE — el usuario envió `#17122b` duplicado por error |
| Morado | `#4a267f` |
| Magenta | `#85207b` |

El logo es un cuadrado redondeado con degradado (oscuro arriba izq → magenta abajo der),
monograma "ia" en naranja con el punto de la "i" separado, y "ipartner" en blanco debajo
en tipografía redondeada geométrica.

**Falta**: el archivo del logo (preferible SVG, para animar por partes). El logo viejo
tampoco está disponible todavía.

## Entorno

- HyperFrames: 21 skills en `.claude/skills`, CLI vía `npx hyperframes@latest`.
- FFmpeg y Node 22 vienen en la imagen.
- **La red bloquea los CDN** (`cdn.jsdelivr.net`, `unpkg.com`) y todo `*.heygen.com`.
  Las plantillas cargan GSAP desde CDN, así que el render falla con
  `sub_timeline_script_failure`. Solución verificada: vendorizar GSAP localmente.

  ```bash
  npm i gsap && mkdir -p vendor && cp node_modules/gsap/dist/gsap.min.js vendor/
  # y apuntar el <script> del index.html a vendor/gsap.min.js
  ```

  El render local es gratis y no consume créditos de HeyGen; el render en la nube de
  HeyGen no es usable por el mismo bloqueo de red.
