# api-contract — formative-project-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /projects | Lista proyectos formativos. |
| POST | /projects | Crea un proyecto formativo. |
| GET | /projects/{id}/deliverables | Lista entregables de un proyecto. |
| GET | /projects/{id}/milestones | Lista hitos de un proyecto. |
| GET | /projects/{id}/dependencies | Lista dependencias de un proyecto. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
