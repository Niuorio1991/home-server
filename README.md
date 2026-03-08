# 🏠 Home-Server: Tu Cine en Casa de forma Sencilla

![Placeholder: Captura principal del panel Homepage mostrando widgets y servicios](/docs/images/homepage_main.png)

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

![Placeholder: Captura del Panel Homepage recién instalado](/docs/images/homepage_clean.png)

¡Aquí verás tu nuevo panel de control (Homepage) con acceso directo a todas las aplicaciones!

---

## 🔗 Paso 5: Configuración Inicial de las Aplicaciones

La primera vez que entres a tu panel, necesitarás dedicar unos de 5 a 10 minutos para hacer las conexiones internas entre todos los programas (para que busquen y descarguen). Esto **solo se hace la primera vez**.

👉 **[ABRIR GUÍA DE CONFIGURACIÓN INICIAL (Paso a Paso) ⚙️](docs/CONFIGURACION_INICIAL.md)**

---

## 🎓 ¿Cómo usarlo y cómo funciona?

Hemos preparado una **[Guía Básica de Uso (Haz clic aquí)](docs/GUIA_BASICA.md)** súper amigable donde te explicamos:
* Cómo funciona la "magia" entre las aplicaciones.
* Cómo pedir y descargar tu primera película.
* Cómo descargar una serie paso a paso.

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
