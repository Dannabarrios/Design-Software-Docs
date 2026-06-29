# events — reporting-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `ReportGenerated` | Un reporte finaliza su generación con éxito. |
| `ReportFailed` | La generación de un reporte falla. |
| `PDFExportReady` | Un exportable PDF está disponible para descarga. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| `AttendanceRecorded` | attendance-trace-service | Actualiza indicadores de asistencia en tableros. |
| `LearnerProgressUpdated` | learner-progress-service | Actualiza indicadores de avance de aprendices. |
| `SessionScheduled` | schedule-service | Consolida datos de sesiones para reportes de horarios. |
| `CohortUpdated` | cohort-offering-service | Actualiza datos de ficha en reportes de oferta formativa. |
