# api-contract — notification-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /notifications | Lista notificaciones con filtros de usuario, estado y fecha. |
| POST | /notifications | Crea y envía una notificación. |
| GET | /notifications/{id} | Consulta una notificación por su identificador. |
| PUT | /notifications/{id}/status | Actualiza el estado de una notificación (leída, archivada). |
| GET | /templates | Lista plantillas de notificación disponibles. |
| POST | /templates | Crea una plantilla de notificación. |
| PUT | /templates/{id} | Actualiza una plantilla existente. |
| GET | /channels | Lista canales de envío configurados. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
- El envío es asíncrono; el estado de entrega se actualiza mediante callback del canal.
