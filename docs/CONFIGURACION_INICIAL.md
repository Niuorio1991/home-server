# ⚙️ Guía de Configuración Inicial (Paso a Paso)

¡Tu servidor ya está encendido! Pero como una casa recién comprada, necesitamos darle las llaves a cada aplicación para que puedan entrar a las habitaciones correctas y hablar entre ellas.

Esta configuración **solo se hace por única vez**. Tómatelo con calma y sigue cada paso al pie de la letra.

---

## 1. 🎬 Jellyfin: Tu Netflix Personal

Jellyfin será el lugar donde **verás** todo tu contenido terminando.

1. Abre tu **Panel Homepage** (`http://localhost:3000` o la IP de tu PC).
2. Haz clic en el ícono de **Jellyfin**.
3. Te aparecerá una pantalla de bienvenida. Elige tu idioma preferred y dale a "Siguiente".
4. **Crea tu usuario:** Inventa un nombre de usuario y una contraseña (¡no la olvides!).
5. **Añadir Bibliotecas de Medios:** (Lo más importante)
   * Haz clic en **"Añadir biblioteca multimedia"**.
   * En **Tipo de contenido**, elige **Películas**.
   * En **Nombre mostrar**, escribe "Películas".
   * Haz clic en el símbolo **`+` (Carpetas)**. 
   * Verás una lista de carpetas del sistema. Busca y selecciona la que se llama **`/media`**. (Es crucial que elijas esta exacta). ¡Felicidades, conectaste tu disco duro!
   * Repite este paso 5, pero eligiendo **Series** como tipo de contenido, y volviendo a seleccionar `/media` (o una subcarpeta `/media/tv` si prefieres separarlas).
6. Continúa dando a "Siguiente" en idioma de metadatos (Español) hasta terminar el Asistente.
7. ¡Listo! Ya tienes tu cuenta. 

*Nota: Por ahora estará vacío, ¡vamos a conseguirle contenido!*

---

## 2. 🧲 Transmission: El Descargador Silencioso

Transmission es quien bajará los archivos por detrás. ¡La buena noticia es que **no funciona solo sino que recibe órdenes** y no necesitas configurarle nada de momento! Las descargas caerán en tu carpeta configurada en el `.env`.

---

## 3. 🕸️ Prowlarr: Añadiendo "Páginas de Búsqueda"

Prowlarr es como Google, pero para archivos de películas (torrents).

1. Vuelve al Panel Homepage y abre **Prowlarr**.
2. No te asustes si está en inglés. Ve al menú de la izquierda y haz clic en **Indexers** (Buscadores) y selecciona **Add Indexer**.
3. Verás una lista gigante. Escribe en su barra de búsqueda nombres de páginas famosas públicas, por ejemplo:
   * Escribe `1337x`. Haz clic en él, baja un poco, y dale a **Save** (Guardar).
   * Vuelve a darle a Add. Escribe `TorrentGalaxy`, haz clic en él y dale a **Save**.
   * Vuelve a darle a Add. Busca la etiqueta o botón que dice **"Public"** para ver una lista sugerida y añade 2 o 3 más al azar (ej. ThePirateBay, YTS). Cuantos más tengas, más oportunidades de encontrar resultados.

---

## 4. 🔗 Conectando Prowlarr con Radarr y Sonarr

Ahora tenemos que decirle a Prowlarr que le entregue los resultados a las otras aplicaciones.

1. **La "Clave Secreta" de Radarr:**
   * Abre **Radarr** desde tu Panel Homepage.
   * Ve a **Settings > General**.
   * Busca un campo larguísimo de letras y números llamado **"API Key"**.
   * Selecciona todo ese texto largo y **cópialo**.
2. **Enganchando en Prowlarr:**
   * Regresa a la pestaña de **Prowlarr**.
   * En el menú izquierdo ve a **Settings** y arriba selecciona la pestaña **Apps**.
   * Haz clic en el botón `+` para añadir una.
   * Elige **Radarr**.
   * En **Prowlarr Server**, asegúrate de que diga `http://prowlarr:9696`.
   * En **Radarr Server**, escribe `http://radarr:7878` (*Es la dirección secreta de Docker*).
   * En el cuadro principal **API Key**, **pega** el código larguísimo que copiaste antes.
   * Haz clic abajo en el botón azul **"Test"**. Debería salir una marca verde. Luego dale a **Save**.
3. **Repite lo mismo para Sonarr:**
   * Abre **Sonarr**, ve a **Settings > General**, copia su API Key.
   * Ve a **Prowlarr > Settings > Apps**, dale al `+`.
   * Elige **Sonarr**.
   * En **Sonarr Server**, escribe `http://sonarr:8989`.
   * Pega la Key, haz Test y dale a Save.

¡Magia! Prowlarr le acaba de enviar mágicamente todos los buscadores a Radarr y Sonarr.

---

## 5. 🤖 Radarr y Sonarr: Enseñándoles a Descargar

Ellos ya saben cómo buscar (gracias a Prowlarr), ahora deben saber a quién mandarle la orden de descarga (Transmission).

**Configurando Radarr:**
1. Ve a la pestaña de **Radarr**.
2. Ve a **Settings** y arriba busca **Download Clients** (Clientes de descarga).
3. Haz clic en el botón `+`.
4. En la lista larga, busca bajo el título "Torrents" el ícono rojo de **Transmission** y hazle clic.
5. Se abrirá una ventana de configuración:
   * En **Name**, déjalo como "Transmission".
   * En **Host** (la dirección de la casa), borra `localhost` y escribe exactamente: `transmission`
   * No necesitas usuario ni contraseña.
6. Haz clic abajo en **Test** (Saldrá un check verde ✅) y luego dale a **Save**.

**Configurando Sonarr:**
Haz exactamente lo mismo. (Settings > Download Clients > + > Transmission > Host: `transmission` > Test > Save).

---

## 6. 📝 Bazarr: Magia de Subtítulos

Bazarr analizará todas tus descargas y buscará automáticamente el subtítulo en tu idioma.

1. Abre **Bazarr** desde el panel.
2. Está vacío. Hay que conectarlo. Ve a **Settings > Sonarr**.
   * En "Address", escribe: `sonarr`
   * En "API Key", pega la misma clave súper larga que sacaste de los ajustes de Sonarr en el Paso 4.
   * Dale Test y Save.
3. Haz lo mismo en **Settings > Radarr**.
   * En "Address", escribe: `radarr`
   * Pega la API key larga de Radarr. Test y Save.
4. **Tu idioma:** Ve a **Settings > Languages**. En la caja que dice "Languages Filter", marca **Spanish (es)** (o tu idioma preferido) y **guardar**.
5. Ve a "Settings > Subtitles" e indica que el idioma por defecto sea Spanish.

---

### ¡Misión Cumplida! 🎉

Tu ecosistema "Home-Server" está al 100% configurado, engrasado y listo para recibir órdenes. 

👉 **¿Listo para descargar tu primera película? Lee nuestra: [GUÍA BÁSICA DE USO: El Ecosistema 🎓 ](GUIA_BASICA.md)**
