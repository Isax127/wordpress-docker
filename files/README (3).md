# Práctica: WordPress con Docker Compose y Jenkins

Curso: Organización de Archivos - UPI

## Que hace el proyecto

Levanta un WordPress con su base de datos MySQL usando docker compose. Los dos contenedores quedan en la misma red (wp-net) y usan volumenes para no perder los datos si se reinician. Las contraseñas y nombres de la base estan en el archivo .env para no dejarlos quemados en el compose.

Despues el despliegue se automatiza con Jenkins usando el Jenkinsfile.

## Como levantarlo

```
docker compose up -d
```

Verificar:

```
docker ps
docker network ls
docker volume ls
```

WordPress queda en http://localhost:8080 (ahi sale el asistente de instalacion).

## Pipeline de Jenkins

Etapas:

1. Checkout del repo desde Git
2. docker compose down (bota el ambiente viejo)
3. docker compose up -d (lo vuelve a levantar)
4. docker ps (para verificar que todo subio)

Con esto cada vez que se hace push al repo se puede redesplegar automatico.
