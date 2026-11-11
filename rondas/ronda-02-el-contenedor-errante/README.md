# Ronda 02 EL CONTENEDOR ERRANTE

## Tema

Crear un microservicio independiente con FastAPI que corra en su propio contenedor Docker.

## Tecnología obligatoria

- Framework FastAPI con el lenguaje Python.
- Docker (el microservicio debe tener su propio `Dockerfile`).
- Base de datos opcional: si la usas, debe ir en un contenedor aparte y levantarse junto al microservicio con Docker Compose.

## Duración

1 a 2 semanas

## Modalidad (solo/equipo)

Solitario

## Requisitos

- El microservicio expone una API REST con al menos un recurso propio (el tema es libre).
- Incluye un endpoint de salud `GET /health` que responda si el servicio está funcionando.
- Tiene un `Dockerfile` funcional y se puede levantar con `docker build` + `docker run` (o con `docker compose up` si usas base de datos).
- La configuración se maneja con variables de entorno: no hay secretos dentro de la imagen, e incluye un `.env.example` y un `.dockerignore`.
- El README del proyecto explica cómo levantarlo y cómo ver la documentación automática de FastAPI (`/docs`).

## Recursos recomendados

### Videos

- [amin espinoza - Aprender lo basico para docker y contendores](https://www.youtube.com/watch?v=UpkbE8FIJwQ)

### Documentación

- [Documentación oficial de FastAPI](https://fastapi.tiangolo.com/es/)
- [FastAPI en contenedores - Docker](https://fastapi.tiangolo.com/es/deployment/docker/)
- [Documentación oficial de Docker](https://docs.docker.com/)
- [Consejos de uso de Docker (guía de La Forja)](../../docs/consejos-uso-docker.md)

## Formato de entrega

Se revisará en asincrónico desde el repositorio del participante, se opinará en el chat general de la comunidad.

## Fecha de inicio y cierre

- Inicio: 11 de noviembre
- Cierre: 25 de noviembre
