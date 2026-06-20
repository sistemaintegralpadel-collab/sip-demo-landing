# SiP! — Landing demo.sip-padel.com

## Qué es
Landing page minimalista para compartir en WhatsApp/redes.
Muestra el logo de SiP!, la frase "¿Tenés WhatsApp? Ya tenés cancha." y un botón
que abre directo el WhatsApp del club demo (Efecto Pádel) con "Hola!" precargado.

Cuando se comparte el link en WhatsApp, se muestra una tarjeta con preview
(imagen + título + descripción), gracias a las meta tags Open Graph en el HTML.

## Archivos
- `index.html` — la landing completa (HTML + CSS inline, sin dependencias externas excepto Google Fonts)
- `sip-logo.png` — el logo de SiP! (formato horizontal, fondo negro)
- `server.js` — servidor Express mínimo para servir el HTML en Railway
- `package.json` — dependencias (solo Express)

## Cómo subir a Railway

1. Crear un repo nuevo en GitHub (ej: `sip-demo-landing`) y subir estos 4 archivos
2. En Railway: New Project → Deploy from GitHub repo → seleccionar `sip-demo-landing`
3. Railway detecta Node.js automático, corre `npm install` y `npm start`
4. Una vez deployado, Railway te da una URL tipo `sip-demo-landing.up.railway.app`

## Cómo conectar el dominio demo.sip-padel.com

1. En Railway: el servicio → Settings → Networking → "Custom Domain"
   Agregar: `demo.sip-padel.com`
   Railway te va a dar un CNAME target (algo como `xxxx.up.railway.app`)

2. En Cloudflare (cuenta piovancl@gmail.com):
   DNS → Add record:
   Type: CNAME
   Name: demo
   Target: (el que te dio Railway)
   Proxy status: DNS only (⚠️ IMPORTANTE — igual que api y bot, NO proxied)

3. Esperar 2-5 minutos a que propague. Probar en el navegador: https://demo.sip-padel.com

## Si querés cambiar el texto o el número de WhatsApp

Buscar en `index.html` la línea con `href="https://wa.me/...`
y reemplazar el número o el texto después de `?text=`.

El texto va URL-encoded (espacios = %20, ! = %21, etc.)
