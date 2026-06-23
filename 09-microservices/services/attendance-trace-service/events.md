# events — attendance-trace-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `TrainingSessionExecuted` | Se ejecuta una sesión de formación. |
| `AttendanceTraceRegistered` | Se registra trazabilidad de asistencia. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| `SchedulePlanned` | schedule-service | Conoce las sesiones programadas a ejecutar. |
