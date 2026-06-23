# events — schedule-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `SchedulePlanned` | Se planifica un horario. |
| `ScheduleChanged` | Cambia un horario existente. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| — | — | El servicio no consume eventos en esta versión. |
