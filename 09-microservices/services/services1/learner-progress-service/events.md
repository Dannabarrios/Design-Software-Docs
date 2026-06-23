# events — learner-progress-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `LearnerProgressUpdated` | Se actualiza el avance de un aprendiz. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| `EvidenceValidated` | evidence-service | Recalcula el avance cuando se valida una evidencia. |
