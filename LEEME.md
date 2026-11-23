# Jesús Argaña Presidente 2028 — guía de edición

Landing page de una sola página, lista para publicar. No necesita servidor ni
instalación: es un archivo HTML con todo adentro (estilos, tipografías e
imágenes), así que podés abrirlo con doble clic y subirlo a cualquier hosting.

```
pagina-politica/
├── index.html          ← la página (todo está acá)
├── LEEME.md            ← esta guía
└── assets/
    ├── candidato.jpg   ← retrato del afiche (respaldo)
    ├── candidato-recorte.png ← figura recortada que usa la página, tal cual
    ├── og-image.jpg    ← imagen 1200×630 para el link compartido (el afiche)
    ├── asuncion-palacio.jpg ← foto del Palacio de López, de fondo en la tapa
    ├── hero.jpg        ← ilustración de multitud (ya no se usa)
    └── fuentes/        ← tipografías originales (Anton, Inter; ya incrustadas)
```

**Fondo de la tapa:** el Palacio de López, con un velo rojo y una retícula fina
encima, y la figura recortada del candidato al centro.

**Movimiento:** la campaña se presenta como **Siempre Habrá un 13 de Enero – LMA**.
El nombre aparece en las firmas del candidato, en el hito de 2026 del recorrido,
en la franja de conceptos, en el pie y en el título de la página. Se edita una
sola vez en `CONFIG.movimiento`, al final del archivo.

**Identidad visual:** sistema de afiche. Rojo sangre `#A50E18` (con `#7A0710`
para los oscuros y `#63050E` para la escena) y blanco, con
Anton (titular condensado) para títulos e Inter para texto. La tapa es una
cabecera roja con el lema en blanco, una cinta blanca con el cierre «Con los
valores intactos» y el retrato recortado sobre la multitud en blanco y negro.
Bordes rectos, cifras en banda negra y sin animaciones decorativas.

---

## 1. Datos ya cargados

La página ya dice **Jesús Argaña — Presidente · ANR · 2028**. Para cambiar
cualquier dato, abrí `index.html`, bajá hasta el final y buscá el bloque
**CONFIG DE CAMPAÑA**:

```js
const CONFIG = {
  candidato: "Jesús Argaña",
  cargo:     "Presidente · ANR · 2028",
  anio:      2028,
  url:       "https://ejemplo.com.py/",       // donde vas a publicar
  correo:    "contacto@ejemplo.com.py",
  whatsapp:  "595981423840",                 // código de país + número, sin + ni espacios
  redes: {
    instagram: "https://instagram.com/",
    facebook:  "https://facebook.com/",
    tiktok:    "https://tiktok.com/",
    x:         "https://x.com/",
    youtube:   "https://youtube.com/"
  },
  handles: {
    instagram: "@usuario",     // ← cambiá por el usuario real
    facebook:  "/pagina",
    tiktok:    "@usuario",
    x:         "@usuario",
    youtube:   "/@canal"
  }
};
```

Con cambiar `candidato`, `cargo`, `url`, `correo` y `whatsapp` se actualizan
solos: el nombre en la sección «El candidato», el botón flotante de WhatsApp,
los links de WhatsApp, el correo y teléfono del pie y los botones de compartir.

## 2. La foto

La página usa **`assets/candidato-recorte.png`** (461×373, fondo transparente),
incrustada en base64 sin ninguna modificación: ni recorte, ni recoloreo, ni
recompresión. Aparece dos veces: como figura sobre la multitud en la tapa y en
la sección «El candidato».

Si la reemplazás por otra, conviene que sea un PNG con fondo transparente y la
misma proporción. Está incrustada, así que además de cambiar el archivo hay que
actualizar el `src="data:image/png;base64,…"` en los dos lugares del HTML (o
pedirme que lo haga yo).

`assets/candidato.jpg` (960×1200) es el retrato del afiche: queda como respaldo
y es el que se usó para la imagen de compartir.

## 3. Qué está cargado y qué es de ejemplo

**Tomado de tu afiche y del dominio público:**

- «Siempre habrá un 13 de enero»: la frase de Luis María Argaña, que remite al
  13 de enero de 1947 y quedó como símbolo del coloradismo tradicionalista.
- Luis María Argaña fundó Reconciliación Colorada en 1992 y fue vicepresidente
  desde agosto de 1998; fue asesinado el 23 de marzo de 1999.
- La ANR reinscribió movimientos para las internas de 2027 (fecha probable:
  diciembre de 2027) y las generales son en 2028.
- Jesús Argaña es hijo de Luis María Argaña y dirigente de la ANR.
- Los ejes del afiche: trabajo para la gente, seguridad en todo el país,
  desarrollo y progreso, bienestar para todos. El lema «Un Paraguay mejor es
  posible» y el cierre «Con la fuerza del pueblo, por un Paraguay más próspero».

**De ejemplo, para reemplazar:**

- Las **6 propuestas** (Salud que llega, Escuelas abiertas, Trabajo que no se va,
  Seguridad en serio, Caja abierta, Campo y producción) son redacción
  genérica: hay que poner el programa real.
- La línea de tiempo «De dónde venimos» es histórica, pero podés ajustarla.
- Los **3 eventos** de la agenda no tienen fecha: dicen «Fecha a confirmar» y el
  botón invita a dejar el contacto («Avisame»). Cuando estén las fechas, cambiá
  el bloque `<div class="fecha fecha--abierta">` de cada tarjeta por
  `<div class="fecha"><b>14</b><span>Mar · 19:00</span></div>`.
- Los handles (`@usuario`, `/pagina`) y los links de redes son marcadores:
  reemplazalos por los reales.
- La franja de conceptos, la cinta «Con los valores intactos» y el sello
  «Presidente 2028» de la tapa son diseño propio.

## 4. Cargar los links reales de las redes

En el HTML, buscá `<div class="redes-grid">` y reemplazá cada
`href="https://instagram.com"` por la dirección del perfil. Los textos que se
muestran se editan en `CONFIG.handles`, al final del archivo.

## 5. Publicar

1. Subí la carpeta completa (con `assets/`) a tu hosting.
2. En el `<head>`, cambiá `og:url`, `og:image`, `twitter:image` y `canonical`
   por tu dominio real. Las imágenes de compartir necesitan direcciones
   completas (`https://…`), si no las redes no las muestran.
3. Pasá el link por el [depurador de Facebook](https://developers.facebook.com/tools/debug/)
   para forzar la vista previa.
4. El formulario no necesita backend: abre el correo del visitante con el
   mensaje ya escrito hacia `CONFIG.correo`.

## 6. Antes de publicar: revisá esto

- [ ] Revisar que el nombre y el cargo estén como los usa la campaña.
- [ ] Revisar `assets/candidato-recorte.png`: tiene que ser la figura oficial.
- [ ] Reemplazar las 6 propuestas por el programa real.
- [ ] Cargar fechas y lugares reales de la agenda.
- [ ] Reemplazar los handles y los links de redes.
- [ ] Completar los links de «Transparencia» del pie.
- [ ] Actualizar `CONFIG.url`, `og:url`, `og:image` y `canonical` con el dominio.
- [ ] Borrar la franja amarilla de aviso (`id="aviso"`).

---

## Detalles técnicos

- **Un solo archivo**: imágenes y tipografías van incrustadas en base64.
  Pesa ~580 KB.
- **Identidad visual**: sistema de afiche. Rojo sangre `#A50E18`, `#7A0710`
  para los oscuros y `#63050E` para la escena, negro `#0B0B0C` y blanco. El retrato va recortado
  sobre una ilustración de multitud en blanco y negro con una retícula de líneas.
- **Tipografías**: Anton (titulares, subset incrustado) e Inter (texto).
- **Accesibilidad**: navegación por teclado, enlace «saltar al contenido»,
  foco visible, textos alternativos y respeto por «reducir movimiento».
- **Sin backend**: el formulario arma un correo con los datos.

## Sobre el contenido político

Esta página la armé con información pública disponible al 23 de noviembre de
2026. Los dichos y propuestas de campaña son responsabilidad del equipo del
candidato. Antes de publicar conviene revisar que cada dato siga vigente y que
la propaganda cumpla con las normas del Tribunal Superior de Justicia Electoral.


---

## ⚡ Mejoras y Optimización Aplicadas (Auditoría 2028)

1. **Favicon SVG incrustado:** Se agregó ícono vectorial rojo con la estrella republicana en `<head>` (sin archivos externos).
2. **Doble canal de captación en el Formulario:** Los voluntarios pueden sumarse enviando sus datos directamente por **WhatsApp** (canal predilecto en Paraguay con mensaje formateado) o por **Correo Electrónico**.
3. **Validación HTML5:** El formulario ahora comprueba que los campos requeridos estén completos antes de abrir WhatsApp o el gestor de correo.
4. **Enlaces dinámicos a Redes Sociales:** Al hacer clic en las tarjetas de Instagram, Facebook, TikTok, X y YouTube, el navegador abre directamente el perfil oficial configurado en `CONFIG.handles` (no la portada genérica).
5. **Formato telefónico flexible:** El formateador de teléfono ahora soporta números tanto de 11 dígitos (líneas fijas/Asunción +595 21...) como de 12 dígitos (móviles +595 981...).
6. **Contraste de color accesible (WCAG AA):** Se ajustó `--gris-3` a `#66666E` para asegurar legibilidad sobre fondo blanco y gris claro.
