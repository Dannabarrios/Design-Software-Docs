# api-contract — parameter-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /catalogs | Lista catálogos base. |
| GET | /catalogs/{id} | Consulta un catálogo. |
| GET | /parameters | Lista parámetros configurables. |
| PUT | /parameters/{id} | Actualiza un parámetro. |
| GET | /calendars | Lista calendarios institucionales. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
