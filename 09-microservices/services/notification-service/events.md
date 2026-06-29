# events — notification-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `NotificationSent` | Una notificación es enviada exitosamente al destinatario. |
| `NotificationFailed` | El envío falla después de los reintentos configurados. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| `SessionScheduled` | schedule-service | Notifica a instructor y aprendices afectados por el horario. |
| `SessionCancelled` | schedule-service | Alerta a los afectados sobre la cancelación de una sesión. |
| `AttendanceAlertTriggered` | attendance-trace-service | Envía alerta de inasistencia a coordinador o instructor. |
| `LearnerAtRisk` | learner-progress-service | Notifica al coordinador sobre un aprendiz con riesgo de reprobación. |
