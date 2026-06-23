# api-contract — institutional-structure-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /regionals | Lista regionales. |
| GET | /centers | Lista centros de formación. |
| POST | /centers | Crea un centro de formación. |
| GET | /venues | Lista sedes. |
| GET | /environments | Lista ambientes. |
| POST | /environments | Crea un ambiente. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
