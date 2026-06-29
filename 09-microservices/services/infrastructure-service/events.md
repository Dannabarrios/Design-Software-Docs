# events — infrastructure-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `ResourceCreated` | Se registra un nuevo recurso físico. |
| `ResourceUpdated` | Se actualizan los datos de un recurso. |
| `ReservationCreated` | Se confirma una reserva de recurso. |
| `ReservationCancelled` | Se cancela una reserva existente. |
| `AvailabilityChanged` | Cambia el estado de disponibilidad de un recurso. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| `SessionScheduled` | schedule-service | Actualiza disponibilidad del ambiente asignado a la sesión. |
| `SessionCancelled` | schedule-service | Libera la disponibilidad del ambiente al cancelar una sesión. |
