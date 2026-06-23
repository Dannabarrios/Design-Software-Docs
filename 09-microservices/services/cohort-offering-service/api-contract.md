# api-contract — cohort-offering-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /fichas | Lista fichas. |
| POST | /fichas | Crea una ficha. |
| GET | /fichas/{id} | Consulta una ficha. |
| GET | /offerings | Lista la oferta formativa. |
| GET | /periods | Lista periodos. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
