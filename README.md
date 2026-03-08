# 🏠 Home-Server: Tu Cine en Casa de forma Sencilla

¡Bienvenido! Este proyecto monta tu propio **Home-Server** para películas y series automático. Es inteligente, se actualiza solo y tiene un panel de control increíble para manejar todo desde un solo lugar.

---

## 🛠️ Paso 1: Instalar "el motor" (Docker)

1.  **Descarga Docker Desktop**: [Windows](https://www.docker.com/products/docker-desktop/) | [Mac](https://www.docker.com/products/docker-desktop/) | [Linux](https://docs.docker.com/desktop/install/linux-install/)
2.  Instálalo y **ábrelo**.

---

## ⚙️ Paso 2: Tu Panel de Control (.env)

1.  Busca el archivo `.env.example` y haz una copia llamada **`.env`**.
2.  Abre el nuevo archivo **`.env`** con el **Bloc de Notas**.
3.  Pon tus rutas:
    *   `MEDIA_PATH`: Carpeta de tus películas.
    *   `DOWNLOADS_PATH`: Carpeta de tus descargas.
**Guarda y cierra.**

---

## 🚀 Paso 3: ¡Encender la magia!

1.  Abre una **Terminal** y escribe `cd ` (con espacio).
2.  **Arrastra esta carpeta** a la terminal y dale a `Enter`.
3.  Escribe: `docker-compose up -d` y dale a `Enter`.

---

## 🖥️ Paso 4: Tu Centro de Mando

Abre tu navegador y entra a:
👉 [**http://localhost:3000**](http://localhost:3000)

---

## ✨ Paso 5 Opcional: Nombres Pro (panel.casa)

Si quieres usar nombres elegantes en lugar de números, abre el archivo `hosts` como administrador y añade esto al final:

```text
127.0.0.1 panel.casa
127.0.0.1 jellyfin.casa
127.0.0.1 radarr.casa
127.0.0.1 sonarr.casa
127.0.0.1 prowlarr.casa
127.0.0.1 descargas.casa
```
¡Ahora puedes entrar a [http://panel.casa](http://panel.casa) directamente!

---

## 🔗 Configuración Inicial (Solo la primera vez)

1.  **Jellyfin:** Crea tu usuario y añade la carpeta `/media`.
2.  **Prowlarr:** Añade buscadores en "Indexers" y conecta Radarr en "Apps" (`http://radarr:7878`).
3.  **Radarr/Sonarr:** En "Settings" > "Download Clients", añade Transmission (nombre del servidor: `transmission`).

---

## 🚀 Características "Pro" Incluidas

*   **Watchtower**: No hagas nada. El sistema se actualiza solo todas las noches.
*   **Proxy Inverso (Caddy)**: Gestiona tus nombres personalizados automáticamente.
*   **Homepage Dashboard**: Una interfaz visual moderna para tu servidor.

---
## 📄 Licencia
Este proyecto es de código abierto bajo la licencia MIT. ¡Siéntete libre de compartirlo y mejorarlo!

*Hecho con ❤️ para que disfrutes de tu cine sin complicaciones.*
