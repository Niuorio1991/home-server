# 🎓 Guía Básica: ¿Cómo funciona tu Home-Server?

¡Felicidades! Ya tienes tu propio servidor de medios funcionando. Pero, ¿cómo se usa exactamente? Esta guía está diseñada para enseñarte paso a paso no solo **cómo** descargar contenido, sino **por qué** funciona como lo hace.

---

## 🧠 Parte 1: Entendiendo la Magia (El Ecosistema)

Tu servidor no es una sola aplicación gigante, sino un equipo de varias aplicaciones especializadas que "hablan" entre sí de forma invisible. Imagina que es como un restaurante:

1.  **Radarr y Sonarr (Los Camareros):** Son las apps a las que tú les pides lo que quieres ver. Radarr es exclusivo para **Películas** y Sonarr para **Series**. Ellos toman tu orden y se encargan de vigilar hasta que esté lista.
2.  **Prowlarr (El Menú/Buscador):** Los camareros no saben dónde buscar por sí solos. Prowlarr es el que tiene la lista de todos los sitios web de descargas (Tórrénts) y les dice a Radarr/Sonarr dónde encontrar la mejor versión de lo que pediste.
3.  **Transmission (El Cocinero):** Una vez que Radarr o Sonarr deciden qué archivo es el mejor, se lo envían a Transmission. Él hace el trabajo pesado: descargar el archivo desde internet a tu disco duro.
4.  **Bazarr (El Traductor):** Mientras se descarga el video, Bazarr va buscando por internet el archivo de texto con los subtítulos exactos para esa versión.
5.  **Jellyfin (El Plato Servido):** Es tu Netflix personal. Una vez que todo está descargado y organizado, Jellyfin lo escanea, le pone la carátula bonita, la descripción, y te permite reproducirlo desde tu tele, móvil o PC.

---

## 🎬 Parte 2: Cómo descargar una Película

¡Vamos a la práctica! Agregar una película es súper sencillo.

1.  Abre **Radarr** desde tu panel web.
![Placeholder: Pantalla de inicio de Radarr](/docs/images/radarr_home.png)
2.  En el menú de la izquierda, haz clic en **"Add New"** (Añadir Nueva).
3.  Usa la barra de búsqueda superior y escribe el nombre de la película (ej. *Dune*, *El Padrino*).
![Placeholder: Resultados de búsqueda en Radarr](/docs/images/radarr_search.png)
4.  Haz clic en la película que buscas. Se abrirá una pequeña ventana con varias opciones:
    *   **Root Folder:** Es la carpeta física donde se guardará. Elígela si no está seleccionada por defecto (usualmente `/movies`).
    *   **Quality Profile:** ¡Muy importante! Aquí decides la calidad que buscas. ¿Quieres que busque la versión ligera de 1080p, o quieres el mastodonte en calidad 4K (UHD)? Elige tu preferencia.
    *   **Monitor:** Déjalo en "Movie". Significa que Radarr estará vigilando en internet hasta que aparezca.
    *   **Availability:** Útil si estás pidiendo una película que está actualmente en cines. Si pides "Released" (Lanzada), esperará a que salga en buena calidad y no descargará las versiones grabadas con cámara de cine.
5.  **El paso clave:** Haz clic en el botón verde **"Add Movie"** (Añadir Película).
    *   Alternativamente, puedes hacer clic en el botón con la lupa 🔍 ("Add + Search"). Esto le dice a Radarr: *"Añade la película y ponte a buscarla a lo loco ahora mismo"*.

Y ya está. Radarr contactará a Prowlarr, Prowlarr le dará los enlaces, Radarr elegirá el mejor según tu perfil de calidad, se lo pasará a Transmission, y en un rato aparecerá mágicamente en Jellyfin.

---

## 📺 Parte 3: Cómo descargar una Serie

El proceso en Sonarr es casi idéntico al de Radarr, pero con una diferencia importante: ¡las series tienen temporadas y episodios!

1.  Abre **Sonarr** desde tu panel de control.
![Placeholder: Pantalla de inicio de Sonarr](/docs/images/sonarr_home.png)
2.  Ve a **"Add New"** y busca la serie.
3.  Al seleccionarla, verás una ventana parecida a la de Radarr, pero con una opción extra clave: **"Monitor"**.
![Placeholder: Ventana de opciones al añadir serie en Sonarr](/docs/images/sonarr_add.png)
    *   **All Episodes:** Sonarr descargará *todo* lo que exista de esa serie. Si es una serie vieja de 10 temporadas, prepárate para descargar cientos de gigas de golpe.
    *   **Future Episodes:** Solo descargará los capítulos nuevos que salgan a partir de hoy. (Ideal para series que estás viendo al día).
    *   **Missing:** Descargará lo que te falte.
    *   **First Season / Latest Season:** Descarga solo la primera o la última temporada.
4.  Haz clic en el botón verde **"Add"**. Si quieres que empiece a buscar los episodios inmediatamente, marca la casilla que tiene una lupa en la misma ventana antes de añadirla.

---

## 📱 Parte 4: Cómo ver tus Películas en la Tele o Móvil

Jellyfin tiene aplicaciones gratuitas para casi cualquier dispositivo moderno. Ya no necesitas copiar tus películas a un pendrive USB.

**⚠️ Paso Previo Obligatorio: Descubrir la IP de tu Computadora (Windows)**
Para que tu tele o móvil se conecten a tu servidor, necesitan saber su "número telefónico" dentro de la casa (la IP Local).
1. En la computadora donde instalaste el servidor, presiona la tecla `Windows` del teclado.
2. Escribe `cmd` y abre la aplicación "Símbolo del sistema".
3. Aparecerá una pantalla negra. Escribe `ipconfig` y pulsa `Enter`.
4. Busca la línea que dice **Dirección IPv4** (Ejemplo: `192.168.1.50`). ¡Despliega esa IP, anótala, porque es tu clave de acceso!

---

1.  **Desde un Smart TV (Android TV, LG WebOS, Samsung Tizen, Roku):**
    *   Ve a la tienda de aplicaciones de tu televisor y busca "Jellyfin".
    *   Descárgala y ábrela.
    *   La tele te pedirá la dirección de tu servidor. Tienes que escribir `http://` seguido de la IP que anotaste y terminar con `:8096`.
    *   *Ejemplo exacto:* Si tu IP era `192.168.1.50`, escribirás: `http://192.168.1.50:8096`
    *   Inicia sesión con el usuario y contraseña que creaste en Jellyfin la primera vez, ¡y a disfrutar!

2.  **Desde un Teléfono Móvil o Tablet (Android / iOS):**
    *   Busca "Jellyfin" en la tienda de aplicaciones de tu móvil.
    *   Sigue exactamente los mismos pasos de la dirección IP (`http://TU_IP:8096`).
    *   *Ventaja extra:* Desde la app del móvil puedes enviar cualquier película a un **Chromecast** conectado a tu tele usando el icono de "Transmitir".

3.  **Desde otro ordenador en tu misma casa:**
    *   Simplemente abre un navegador web (Chrome, Edge).
    *   Escribe `http://TU_IP:3000` para ver tu panel completo, o `http://TU_IP:8096` para ir directo a las películas.

*Nota:* Para acceder desde *fuera* de tu casa (por ejemplo, viendo una película en el bus usando tus datos del móvil), requiere configurar redireccionamientos en tu router (port forwarding), lo cual es un poco más avanzado. ¡De momento, disfruta tu Netflix casero con los que estén conectados a tu mismo WiFi!

---

## 💡 Tips Adicionales (Nivel Universitario)

*   **¿Qué pasa si la película se descargó en otro idioma?** Radarr y Sonarr usan "Perfiles de Idioma" (Language Profiles). Por defecto suelen buscar contenido original. En los ajustes ("Settings > Profiles") puedes crear un perfil que priorice el audio "Spanish" para que el sistema busque siempre esas versiones primero.
*   **Actualizaciones Automáticas:** A veces sale una película en mala calidad (Web-DL 720p). Si le dices a Radarr que tu ideal es 1080p, Radarr descargará primero la de 720p para que la vayas viendo, pero seguirá buscando silenciosamente meses después. Cuando alguien suba la copia en 1080p, la descargará y reemplazará la mala automáticamente. ¡Es así de inteligente!
*   **Espacio en Disco:** Ten cuidado con el "Quality Profile" y de no poner a descargar todas las temporadas de *Los Simpsons* a la vez, o te quedarás sin disco duro rápidamente.
