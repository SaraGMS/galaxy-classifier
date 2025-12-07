# Guía de Despliegue en Render

Esta guía explica cómo desplegar la API Flask del proyecto `galaxy-classifier` en Render paso a paso.

---

## 1. Prepara tu repositorio
- Asegúrate de que tu proyecto esté en GitHub y sea accesible.
- El repositorio debe contener:
  - `requirements.txt` con todas las dependencias.
  - `Dockerfile` (opcional, pero recomendado para mayor control).
  - Código fuente de la API (por ejemplo, en `src/api/app.py`).

## 2. Crea una cuenta en Render
- Ve a https://render.com y regístrate o inicia sesión.

## 3. Conecta tu repositorio
- Haz clic en "New +" > "Web Service".
- Elige "Connect a repository" y selecciona tu repo de GitHub.

## 4. Configura el servicio
- **Name:** Elige un nombre para tu servicio.
- **Environment:** Python 3 (o Docker si usas Dockerfile).
- **Build Command:**
  - Si usas Dockerfile: déjalo vacío.
  - Si NO usas Dockerfile: `pip install -r requirements.txt`
- **Start Command:**
  - Si usas Dockerfile: déjalo vacío.
  - Si NO usas Dockerfile: `gunicorn src.api.app:app`
- **Branch:** Elige la rama a desplegar (por ejemplo, `main` o `develop`).
- **Root Directory:** Si tu código está en una subcarpeta, indícalo (por ejemplo, `src/`).

## 5. Variables de entorno (opcional)
- Añade variables de entorno necesarias (por ejemplo, claves, rutas, etc.).

## 6. Despliega
- Haz clic en "Create Web Service".
- Render instalará dependencias y lanzará tu API.
- Espera a que el estado sea "Live".

## 7. Prueba tu API
- Render te dará una URL pública (por ejemplo, `https://galaxy-classifier.onrender.com`).
- Prueba los endpoints usando Postman, curl o tu frontend.

---

## Consejos
- Si usas Docker, asegúrate de que el `Dockerfile` exponga el puerto 10000 o el que Render indique.
- Si tienes una base de datos, crea el servicio correspondiente en Render y configura las variables de entorno.
- Consulta los logs en Render para depurar errores.

---

## Recursos
- [Documentación oficial de Render](https://render.com/docs/deploy-flask)
- [Ejemplo de despliegue Flask en Render](https://render.com/docs/deploy-flask)

---

¡Listo! Tu API debería estar accesible en la nube.