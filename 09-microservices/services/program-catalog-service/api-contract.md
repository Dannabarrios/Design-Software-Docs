# api-contract — program-catalog-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /programs | Lista programas de formación. |
| POST | /programs | Crea un programa de formación. |
| GET | /programs/{id} | Consulta un programa por su identificador. |
| PUT | /programs/{id} | Actualiza un programa de formación. |
| GET | /programs/{id}/competencies | Lista las competencias de un programa. |
| GET | /competencies/{id}/raps | Lista los RAP de una competencia. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.