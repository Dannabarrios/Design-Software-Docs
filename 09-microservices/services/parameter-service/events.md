# events — parameter-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `ParameterUpdated` | Se actualiza un parámetro. |
| `CalendarUpdated` | Se actualiza un calendario institucional. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| — | — | El servicio no consume eventos en esta versión. |
