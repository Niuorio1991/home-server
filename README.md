# 🏠 Home-Server: Tu Cine en Casa de forma Sencilla

¡Bienvenido! Este proyecto monta tu propio **Home-Server** para películas y series automático. Es inteligente, se actualiza solo y tiene un panel de control increíble para manejar todo desde un solo lugar.

---

## 🛠️ Paso 1: Instalar "el motor" (Docker)

Docker es el programa base que hará funcionar todas las aplicaciones en tu servidor sin que tengas que instalarlas una por una de forma complicada.

1.  **Descarga Docker Desktop**: [Windows](https://www.docker.com/products/docker-desktop/) | [Mac](https://www.docker.com/products/docker-desktop/) | [Linux](https://docs.docker.com/desktop/install/linux-install/)
2.  Instálalo como cualquier otro programa y **ábrelo** (déjalo funcionando en segundo plano).

---

## ⚙️ Paso 2: Tu Panel de Control Personal (.env)

El archivo `.env` guarda tus configuraciones personales de forma segura.

1.  En la carpeta de este proyecto, busca el archivo llamado `.env.example`.
2.  Haz una copia de ese archivo y renómbralo a **`.env`** (asegúrate de que empiece con un punto).
3.  Abre el nuevo archivo **`.env`** con el **Bloc de Notas** (o cualquier editor de texto simple).
4.  Configura tus carpetas principales:
    *   `MEDIA_PATH=`: Escribe aquí la ruta a la carpeta donde guardarás tus películas y series. Ejemplo en Windows: `C:\Users\tu_usuario\Videos` o Mac: `/Users/tu_usuario/Movies`.
    *   `DOWNLOADS_PATH=`: Escribe aquí la ruta donde quieres que se descarguen los archivos temporalmente.
5.  **Guarda y cierra** el archivo.

---

## 🚀 Paso 3: ¡Encender la magia!

1.  Abre la **Terminal** (Mac/Linux) o **Símbolo del sistema / PowerShell** (Windows).
2.  Navega hasta la carpeta de este proyecto usando el comando `cd`. *Truco: Puedes escribir `cd `, dejar un espacio, y luego **arrastrar esta carpeta** a la terminal y pulsar `Enter`.*
3.  Para encender todo, escribe el siguiente comando y pulsa `Enter`:
    ```bash
    docker-compose up -d
    ```
4.  Espera unos minutos a que descargue todo (solo tarda la primera vez).

---

## 🖥️ Paso 4: Tu Centro de Mando

Una vez que la terminal termine, abre tu navegador web favorito y entra a esta dirección:
👉 [**http://localhost:3000**](http://localhost:3000)

¡Aquí verás tu nuevo panel de control (Homepage) con acceso directo a todas las aplicaciones!

---

## 🔗 Paso 5: Configuración Inicial de las Aplicaciones

La primera vez que entres, necesitarás hacer unas conexiones rápidas entre las apps (solo se hace una vez):

1. **Jellyfin (Tu Netflix Personal):**
   * Entra desde tu panel web y sigue el asistente para crear tu usuario.
   * Al agregar tus bibliotecas (Películas o Series), selecciona la carpeta que se llama `/media`.

2. **Transmission (Las descargas):**
   * Listo para usarse. Gestionará las descargas en segundo plano.

3. **Radarr (Películas) y Sonarr (Series):**
   * Ve a "Settings" (Ajustes) > "Download Clients" (Clientes de descarga).
   * Añade "Transmission". Donde te pide el "Host", simplemente escribe `transmission`.

4. **Prowlarr (El buscador):**
   * Entra a "Indexers" y añade un par de sitios gratuitos (ej. TorrentGalaxy, 1337x).
   * Ve a "Settings" > "Apps" y añade a **Radarr** y **Sonarr** para que usen lo que encuentra.
   * *El secreto:* En la URL (dirección) de cada uno pon `http://radarr:7878` y `http://sonarr:8989`. Te pedirá su API Key, la puedes sacar de los Ajustes > General de Radarr y Sonarr.

5. **Bazarr (Subtítulos):**
   * Ve a ajustes, conéctalo a Sonarr (`http://sonarr:8989`) y Radarr (`http://radarr:7878`). Configura tus idiomas preferidos (ej. Español) y ¡descargará los subtítulos por magia!

---

## ✨ Bonus: Direcciones "Pro" (Opcional)

Si prefieres usar nombres elegantes en tu navegador en lugar de números o el panel:

1.  Abre el archivo `hosts` de tu ordenador como **Administrador**:
    *   **Windows:** `C:\Windows\System32\drivers\etc\hosts`
    *   **Mac/Linux:** `/etc/hosts`
2.  Añade estas líneas al final del archivo:

```text
127.0.0.1 panel.casa
127.0.0.1 jellyfin.casa
127.0.0.1 radarr.casa
127.0.0.1 sonarr.casa
127.0.0.1 prowlarr.casa
127.0.0.1 descargas.casa
127.0.0.1 subtitulos.casa
```
¡Listo! Podrás usar esos enlaces directamente (jellyfin.casa, panel.casa, etc.).

---

## 🌟 Todas las Herramientas Incluidas

*   **Jellyfin**: Reproduce tus películas donde quieras (SmartTV, móvil, PC) sin pagar a empresas externas.
*   **Radarr/Sonarr**: Buscan, descargan y organizan automáticamente las películas y series que les pidas.
*   **Transmission**: Gestor de descargas de Torrents súper ligero.
*   **Prowlarr**: Gestiona los buscadores para que Radarr/Sonarr puedan encontrar lo último.
*   **Bazarr**: Se encarga de descargar el archivo `.srt` (subtítulo) correcto para tu idioma.
*   **Homepage**: Un panel visual hermoso para tener todo a un click.
*   **Watchtower**: Se actualiza todo solo mientras duermes. ¡Mantenimiento cero!

---
## 📄 Licencia
Este proyecto es de código abierto bajo la licencia MIT. ¡Siéntete libre de compartirlo y mejorarlo!

*Hecho con ❤️ para que disfrutes de tu cine sin complicaciones.*
