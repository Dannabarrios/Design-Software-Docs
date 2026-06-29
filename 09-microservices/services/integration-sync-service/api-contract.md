# api-contract — integration-sync-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /master-sources | Lista las fuentes maestras externas configuradas. |
| POST | /master-sources | Registra una nueva fuente maestra. |
| GET | /master-sources/{id} | Consulta una fuente maestra por su identificador. |
| GET | /sync-jobs | Lista trabajos de sincronización con filtros de estado y fecha. |
| POST | /sync-jobs | Lanza un trabajo de sincronización manual. |
| GET | /sync-jobs/{id} | Consulta el estado de un trabajo de sincronización. |
| GET | /sync-logs | Consulta el registro histórico de sincronizaciones. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
- La sincronización es unidireccional: de la fuente externa hacia el sistema interno; nunca se escribe de vuelta a SOFIA Plus.
