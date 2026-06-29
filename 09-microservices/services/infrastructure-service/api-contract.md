# api-contract — infrastructure-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Contrato de API del servicio. La especificación formal OpenAPI se ubica en `07-api/contracts/openapi/`.

## Endpoints principales

| Método | Ruta | Descripción |
|--------|------|-------------|
| GET | /resources | Lista recursos físicos registrados. |
| POST | /resources | Registra un nuevo recurso físico. |
| GET | /resources/{id} | Consulta un recurso por su identificador. |
| PUT | /resources/{id} | Actualiza datos de un recurso. |
| GET | /inventories | Lista el inventario base de recursos. |
| POST | /inventories | Registra un ítem de inventario. |
| GET | /availabilities | Consulta disponibilidad de ambientes en un rango de fechas. |
| POST | /reservations | Crea una reserva de recurso o ambiente. |
| DELETE | /reservations/{id} | Cancela una reserva existente. |

## Reglas

- Todas las operaciones propagan `correlation_id`.
- El acceso a los datos solo se realiza por estos endpoints; ningún otro servicio accede a la base de datos directamente.
- La disponibilidad se actualiza automáticamente al confirmar o cancelar una reserva.
