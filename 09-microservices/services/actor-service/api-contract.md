# api-contract — actor-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /instructors | Lista instructores. |
| POST | /instructors | Crea un instructor. |
| GET | /learners | Lista aprendices. |
| POST | /learners | Crea un aprendiz. |
| GET | /coordinators | Lista coordinadores. |
| GET | /actors/{id} | Consulta un actor por su identificador. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
