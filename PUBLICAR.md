# Cómo publicar la página y abrirla desde las redes

La página que tenés (`index.html` o `Jesus-Argana-Presidente-2028.html`) es un
archivo suelto. Sirve para mandar por WhatsApp como documento, pero **las redes
sociales no pueden abrir un archivo adjunto**: para que el link se abra en el
navegador de cualquiera hace falta que esté publicado en internet.

Son tres pasos y no hace falta saber programar.

---

## Paso 1 · Elegir dónde publicarla

Cualquiera de estas tres opciones funciona. Las tres dan un link del tipo
`https://algo.netlify.app` o `https://tu-dominio.com.py`.

### Opción A — Netlify Drop (la más rápida, gratis)

1. Entrá a **https://app.netlify.com/drop**
2. Arrastrá la **carpeta `pagina-politica` completa** (no el archivo suelto) a
   la zona que dice «Drag and drop your site folder here».
3. En unos segundos te da un link. Ya está publicada.
4. Si querés un nombre lindo: *Site settings → Change site name* →
   por ejemplo `argana2028` → queda `https://argana2028.netlify.app`.
5. Para usar tu dominio propio: *Domain settings → Add custom domain*.

Sin cuenta podés probar; con cuenta gratis (mail + contraseña) el sitio no
expira.

### Opción B — GitHub Pages (gratis, más técnico)

1. Creá una cuenta en **https://github.com**
2. *New repository* → nombre `argana2028` → **Public** → *Create*.
3. *Add file → Upload files* → subí `index.html` y la carpeta `assets`.
4. *Settings → Pages* → en *Branch* elegí **main** y `/root` → *Save*.
5. En un par de minutos queda en `https://TU-USUARIO.github.io/argana2028/`.

### Opción C — tu hosting actual

Si la campaña ya tiene dominio y panel de control (cPanel, Plesk, FTP):

1. Subí todo el contenido de la carpeta `pagina-politica` a la carpeta pública
   del hosting: normalmente se llama `public_html` o `www`.
2. El archivo `index.html` tiene que quedar en la raíz de esa carpeta.
3. La página se abre sola en `https://tudominio.com.py`.

---

## Paso 2 · Cambiar las direcciones de ejemplo

Los buscadores y las redes necesitan la dirección **completa** de la imagen para
mostrar la tarjeta de vista previa. Si queda `ejemplo.com.py`, no se ve nada.

Abrí el `index.html` con un editor de texto (Bloc de notas, Notepad++, VS Code)
y en las **primeras 40 líneas** buscá estas cinco y reemplazá el dominio por el
tuyo real:

| Línea | Qué dice ahora | Qué tenés que poner |
|---|---|---|
| `canonical` | `https://ejemplo.com.py/` | tu dominio, igual que abajo |
| `og:image` | `https://ejemplo.com.py/assets/og-image.jpg` | `https://TU-DOMINIO/assets/og-image.jpg` |
| `og:url` | `https://ejemplo.com.py/` | `https://TU-DOMINIO/` |
| `twitter:image` | `https://ejemplo.com.py/assets/og-image.jpg` | igual que `og:image` |
| `twitter:site` | `@usuario` | la cuenta de X de la campaña |

También conviene revisar el bloque `CONFIG`, al final del archivo, para el
correo y el WhatsApp.

---

## Paso 3 · Ver que la vista previa funcione

Cuando ya esté publicada, pasá el link por el depurador de Facebook:

**https://developers.facebook.com/tools/debug/**

Pegás la dirección, tocás *Debug* y después *Scrape Again*. Te va a mostrar
la tarjeta que van a ver tus contactos: título, descripción e imagen 1200×630.
WhatsApp y Telegram usan los mismos datos, así que si ahí se ve bien, se ve bien
en todos lados.

---

## Qué pasa en cada red

- **WhatsApp:** lo que conviene es mandar el **link**, no el archivo. Al pegarlo
  aparece la tarjeta con la imagen y el título; al tocarla se abre en el
  navegador del teléfono. Si mandás el `.html` como documento, el contacto lo
  tiene que guardar y abrir a mano, y en iPhone muchas veces ni siquiera aparece.
- **Facebook e Instagram:** pegás el link en el post o en la bio. Instagram no
  permite links en los posts, solo en la bio y en las historias (con el sticker
  de enlace).
- **X / Twitter:** pegás el link y se arma la tarjeta. Se ve mejor si cargaste
  `twitter:site` con la cuenta.
- **TikTok:** el link no se puede tocar en el video; va en la bio.

---

## Lo que NO hace falta

- No hace falta base de datos ni servidor especial: es un archivo estático.
- No hace falta que nadie instale nada.
- La página no envía datos a ningún lado; el formulario abre el correo de quien
  lo completa.

---

## Resumen en tres líneas

1. Subí la carpeta a Netlify Drop y obtené un link.
2. Reemplazá `ejemplo.com.py` por ese dominio en las cinco líneas del `<head>`.
3. Compartí el link, no el archivo.
