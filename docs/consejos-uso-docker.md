# 🐳 Consejos de uso de Docker

Guía rápida con lo esencial de Docker para las rondas de **La Forja del Código** que lo requieran (contenedores, microservicios, Docker Compose, etc.). No pretende ser un curso completo, sino un resumen práctico de los comandos y conceptos que más vas a usar.

## Índice

- [Conceptos básicos](#conceptos-básicos)
- [Instalación](#instalación)
- [Comandos esenciales](#comandos-esenciales)
- [El Dockerfile](#el-dockerfile)
- [Docker Compose](#docker-compose)
- [.dockerignore](#dockerignore)
- [Buenas prácticas rápidas](#buenas-prácticas-rápidas)
- [Errores comunes](#-errores-comunes)
- [Documentación sugerida](#-documentación-sugerida)

---

## Conceptos básicos

| Término | Qué es |
|---|---|
| **Imagen** | Plantilla de solo lectura con todo lo necesario para correr tu app (código, dependencias, sistema base) |
| **Contenedor** | Una instancia en ejecución de una imagen — es tu app corriendo, aislada del resto del sistema |
| **Dockerfile** | Archivo con las instrucciones para construir tu propia imagen |
| **Docker Compose** | Herramienta para levantar varios contenedores juntos (ej. app + base de datos) con un solo comando |
| **Volumen** | Espacio de almacenamiento persistente, para que tus datos no se pierdan al borrar un contenedor |
| **Registry** | Repositorio de imágenes, como Docker Hub (el "GitHub" de las imágenes) |

## Instalación

Descarga **Docker Desktop** (incluye Docker Engine + Compose):
👉 https://www.docker.com/products/docker-desktop/

Verifica que quedó instalado:
```bash
docker --version
docker compose version
```

## Comandos esenciales

### Imágenes

```bash
docker images                      # Ver imágenes descargadas localmente
docker pull <imagen>                # Descargar una imagen (ej. docker pull python:3.12)
docker build -t nombre-app .        # Construir una imagen desde tu Dockerfile
docker rmi <imagen>                  # Eliminar una imagen
```

### Contenedores

```bash
docker run <imagen>                          # Crear y correr un contenedor
docker run -d <imagen>                        # Correrlo en segundo plano (detached)
docker run -p 8000:8000 <imagen>              # Mapear puerto local:contenedor
docker run --env-file .env <imagen>           # Pasar variables de entorno desde un archivo
docker ps                                     # Ver contenedores corriendo
docker ps -a                                  # Ver TODOS los contenedores (incluso detenidos)
docker stop <id-o-nombre>                     # Detener un contenedor
docker start <id-o-nombre>                    # Volver a iniciar uno detenido
docker rm <id-o-nombre>                       # Eliminar un contenedor
```

### Inspección y debug

```bash
docker logs <id-o-nombre>              # Ver los logs de un contenedor
docker logs -f <id-o-nombre>           # Ver logs en tiempo real (follow)
docker exec -it <id-o-nombre> bash     # Entrar a una terminal dentro del contenedor
docker inspect <id-o-nombre>           # Ver toda la info detallada del contenedor
```

## El Dockerfile

Ejemplo básico para una app Python (Django/FastAPI):

```dockerfile
# Imagen base
FROM python:3.12-slim

# Directorio de trabajo dentro del contenedor
WORKDIR /app

# Copiar dependencias primero (aprovecha el cache de Docker)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copiar el resto del código
COPY . .

# Puerto que expone la app
EXPOSE 8000

# Comando para correr la app
CMD ["python", "manage.py", "runserver", "0.0.0.0:8000"]
```

> 💡 **Tip:** copia primero los archivos de dependencias (`requirements.txt`, `package.json`) y recién después el resto del código. Así Docker reutiliza el cache de la capa de instalación si solo cambiaste código, no dependencias — builds mucho más rápidos.

## Docker Compose

Para levantar tu app + base de datos juntas. Ejemplo con Django + PostgreSQL:

```yaml
# docker-compose.yml
services:
  web:
    build: .
    ports:
      - "8000:8000"
    env_file:
      - .env
    depends_on:
      - db

  db:
    image: postgres:16
    environment:
      POSTGRES_DB: ${DB_NAME}
      POSTGRES_USER: ${DB_USER}
      POSTGRES_PASSWORD: ${DB_PASSWORD}
    volumes:
      - postgres_data:/var/lib/postgresql/data

volumes:
  postgres_data:
```

Comandos básicos de Compose:

```bash
docker compose up                  # Levantar todos los servicios
docker compose up -d               # Levantarlos en segundo plano
docker compose up --build          # Reconstruir imágenes antes de levantar
docker compose down                # Detener y eliminar los contenedores
docker compose down -v             # Igual, pero también borra los volúmenes (¡cuidado, borra datos!)
docker compose logs -f             # Ver logs de todos los servicios en vivo
docker compose ps                  # Ver estado de los servicios
```

## .dockerignore

Igual que `.gitignore`, pero para que Docker no copie archivos innecesarios (o sensibles) dentro de la imagen:

```
.env
__pycache__/
*.pyc
node_modules/
.git/
.gitignore
README.md
```

> 🔐 **Seguridad:** el `.env` nunca debe copiarse dentro de la imagen con `COPY`. Las variables de entorno se pasan en tiempo de ejecución con `--env-file` o `env_file` en Compose, no se "hornean" dentro de la imagen.

## Buenas prácticas rápidas

- Usa imágenes base `-slim` o `-alpine` cuando puedas: pesan menos y son más rápidas de construir.
- Nunca hardcodees contraseñas o claves directo en el `Dockerfile` o `docker-compose.yml` — usa variables de entorno.
- Un contenedor, una responsabilidad: evita meter la app y la base de datos en el mismo contenedor.
- Corre `docker ps -a` de vez en cuando y limpia contenedores viejos con `docker container prune`.
- Si tu build tarda mucho, revisa el orden de las instrucciones en tu Dockerfile (aprovecha el cache).

## ⚠️ Errores comunes

| Error | Causa probable |
|---|---|
| `port is already allocated` | Ya tienes algo corriendo en ese puerto local. Cambia el mapeo (`-p 8001:8000`) o libera el puerto |
| `Cannot connect to the Docker daemon` | Docker Desktop no está abierto/corriendo |
| La app no conecta a la base de datos | En Compose, usa el **nombre del servicio** (ej. `db`) como host, no `localhost` |
| Cambios en el código no se reflejan | Si no usas volúmenes en desarrollo, hay que reconstruir la imagen (`docker compose up --build`) |
| La imagen pesa demasiado | Revisa que no estés copiando `node_modules/`, `.git/` u otros archivos pesados innecesarios (usa `.dockerignore`) |

---

## 📚 Documentación sugerida

- [Docker - Documentación oficial](https://docs.docker.com/)
- [Docker Compose - Documentación oficial](https://docs.docker.com/compose/)

## 📺 Videos sugeridos

- [amin espinoza - Aprender lo basico para docker y contendores](https://www.youtube.com/watch?v=UpkbE8FIJwQ)
