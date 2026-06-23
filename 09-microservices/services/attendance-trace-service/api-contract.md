# api-contract — attendance-trace-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| POST | /executions | Registra la ejecución real de una sesión. |
| GET | /executions/{id} | Consulta una ejecución. |
| POST | /attendance | Registra asistencia. |
| POST | /incidents | Registra una novedad o incidencia. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
