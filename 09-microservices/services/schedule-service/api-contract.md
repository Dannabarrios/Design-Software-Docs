# api-contract — schedule-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /schedules | Lista horarios. |
| POST | /schedules | Crea un horario. |
| GET | /sessions | Lista sesiones programadas. |
| POST | /assignments | Asigna instructor/ambiente/ficha a una sesión. |
| GET | /conflicts | Lista conflictos detectados. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
