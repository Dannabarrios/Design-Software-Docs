# Patrones de comunicación

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Principios

- Cada microservicio publica los eventos de dominio relevantes.
- La integración entre servicios no depende de joins entre bases de datos.
- Ningún servicio accede a las tablas internas de otro; solo por API o eventos.
- Para trazabilidad se propaga `correlation_id`, `run_id`, `actor_id` y `source_service` cuando aplique.

## Síncrona (REST / gRPC)

Comunicación directa servicio a servicio para operaciones que requieren respuesta inmediata. Se realiza a través de los contratos expuestos por cada servicio (API), nunca por acceso directo a datos. Todas las llamadas propagan el `correlation_id` para mantener la trazabilidad distribuida.

## Asíncrona (eventos)

Comunicación basada en eventos de dominio para desacoplar servicios y soportar trazabilidad. Cada evento debe incluir como mínimo: `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

Eventos transversales sugeridos:

| Evento | Descripción |
|--------|-------------|
| `SchedulePlanned` | Se planificó un horario. |
| `ScheduleChanged` | Cambió un horario existente. |
| `TrainingSessionExecuted` | Se ejecutó una sesión de formación. |
| `AttendanceTraceRegistered` | Se registró trazabilidad de asistencia. |
| `EvidenceSubmitted` | Se entregó una evidencia. |
| `EvidenceValidated` | Se validó una evidencia. |
| `LearnerProgressUpdated` | Se actualizó el avance de un aprendiz. |
| `FormativeProjectMilestoneReached` | Se alcanzó un hito de un proyecto formativo. |
| `PdfGenerationRequested` | Se solicitó la generación de un PDF. |
| `PdfGenerated` | Se generó un PDF. |
| `WorkflowTransitioned` | Una máquina de estados cambió de estado. |
| `PolicyViolationDetected` | Se detectó una violación de política. |
| `AuditEvidenceRegistered` | Se registró evidencia de auditoría. |

## Resiliencia

Para tolerar fallos en la comunicación entre servicios se aplican patrones de circuit breaker, retry con backoff y timeout en las llamadas síncronas. En la comunicación asíncrona se asume consistencia eventual y se diseñan los consumidores para ser idempotentes, evitando efectos duplicados ante reentregas de eventos.