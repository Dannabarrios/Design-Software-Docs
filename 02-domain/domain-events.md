# Eventos de dominio

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Catálogo de eventos de dominio del sistema. Los eventos desacoplan los servicios y soportan la trazabilidad distribuida. Cada evento incluye como mínimo: `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

Fuente: [`09-microservices/communication-patterns.md`](../09-microservices/communication-patterns.md).

## Catálogo de eventos

| Evento | Servicio que lo publica | Descripción |
|--------|------------------------|-------------|
| `SchedulePlanned` | `schedule-service` | Se planificó un horario de formación para una ficha, instructor y ambiente. |
| `ScheduleChanged` | `schedule-service` | Se modificó un horario existente (cambio de ambiente, instructor, bloque u horario). |
| `TrainingSessionExecuted` | `attendance-trace-service` | Se ejecutó una sesión de formación; confirma que la sesión ocurrió en la realidad. |
| `AttendanceTraceRegistered` | `attendance-trace-service` | Se registró la trazabilidad de asistencia de una sesión (lista de presentes, novedades). |
| `EvidenceSubmitted` | `evidence-service` | Un aprendiz entregó una evidencia vinculada a un RAP y proyecto formativo. |
| `EvidenceValidated` | `evidence-service` | Un instructor validó una evidencia entregada por un aprendiz. |
| `LearnerProgressUpdated` | `learner-progress-service` | Se actualizó el avance de un aprendiz en su ficha a partir de una evidencia o validación. |
| `FormativeProjectMilestoneReached` | `formative-project-service` | Un proyecto formativo alcanzó un hito definido en su planificación. |
| `PdfGenerationRequested` | `reporting-service` | Se solicitó la generación de un documento PDF (acta, reporte, exportable). |
| `PdfGenerated` | `reporting-service` | Se completó la generación de un documento PDF y está disponible para descarga. |
| `WorkflowTransitioned` | Transversal (servicio con máquina de estados) | Una entidad con flujo de estados cambió de estado (ej: horario, evidencia, proyecto). |
| `PolicyViolationDetected` | `audit-compliance-service` | Se detectó una acción que viola una política de seguridad, retención o cumplimiento. |
| `AuditEvidenceRegistered` | `audit-compliance-service` | Se registró una evidencia de auditoría inmutable para una acción del sistema. |

## Flujos de eventos representativos

### Ejecución de sesión y trazabilidad

```
schedule-service          → SchedulePlanned
attendance-trace-service  → TrainingSessionExecuted
attendance-trace-service  → AttendanceTraceRegistered
```

### Entrega y validación de evidencia

```
evidence-service          → EvidenceSubmitted
evidence-service          → EvidenceValidated
learner-progress-service  → LearnerProgressUpdated
```

### Generación de reporte

```
(cualquier servicio)      → PdfGenerationRequested
reporting-service         → PdfGenerated
```
