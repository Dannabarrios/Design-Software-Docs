# Entorno local de desarrollo

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Lineamientos para levantar el entorno local de desarrollo del sistema. El entorno debe ser reproducible: cualquier miembro del equipo debe poder clonarlo y ejecutarlo sin pasos manuales adicionales (RNF-010).

## Requisitos base

Antes de levantar el entorno, verificar que estén instalados:

| Herramienta | Propósito |
|-------------|-----------|
| Docker | Ejecutar cada microservicio y MongoDB en contenedores aislados. |
| Git | Clonar el repositorio y trabajar con la estrategia de ramas. |

No se instalan dependencias directamente en la máquina del desarrollador; todo corre dentro de contenedores.

## Estructura de contenedores

El entorno local replica la arquitectura del sistema:

- Cada uno de los 16 microservicios corre en su propio contenedor Docker.
- Una instancia MongoDB corre en un contenedor dedicado, accesible por todos los servicios a través de la red de contenedores.
- Un archivo de composición de contenedores (`docker-compose` o equivalente) define todos los servicios, sus dependencias de arranque y la red compartida.
- El arranque del entorno completo se realiza con un único comando.

## Variables de entorno

Cada servicio lee su configuración desde variables de entorno. Estas nunca se almacenan en el código fuente ni en el repositorio.

| Variable (ejemplo conceptual) | Descripción |
|-------------------------------|-------------|
| `DB_URI` | Cadena de conexión a la instancia MongoDB local. |
| `SERVICE_PORT` | Puerto en el que escucha el servicio. |
| `JWT_SECRET` | Clave para emisión y validación de tokens (solo `auth-service`). |
| `CORRELATION_ID_HEADER` | Nombre del encabezado para `correlation_id` (por convención: `X-Correlation-ID`). |

Cada servicio tiene un archivo de ejemplo (`.env.example`) que documenta las variables necesarias sin valores reales. El desarrollador copia ese archivo a `.env` y completa los valores locales. Los archivos `.env` están excluidos del repositorio.

## Clonar y trabajar el repositorio

El repositorio de documentación sigue la estrategia de ramas definida en [`00-governance/git-conventions.md`](../00-governance/git-conventions.md):

```bash
# Clonar el repositorio
git clone <url-del-repositorio>
cd <nombre-del-repositorio>

# Actualizar la rama base antes de crear una rama de trabajo
git checkout dev
git pull origin dev

# Crear la rama de trabajo para la historia de usuario asignada
git checkout -b hu-<numero>-dev
```

Todo trabajo se realiza en ramas `hu-*-dev` y se integra a `dev` mediante Pull Request. No se hace push directo a `dev`, `qa` ni `main`.

## Arranque del entorno

```bash
# Levantar todos los servicios y MongoDB
docker compose up

# Levantar en segundo plano
docker compose up -d

# Detener el entorno
docker compose down
```

El primer arranque descarga las imágenes necesarias. Los arranques posteriores reutilizan las imágenes en caché, reduciendo el tiempo de inicio.
