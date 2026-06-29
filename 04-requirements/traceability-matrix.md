# Matriz de trazabilidad

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Relaciona cada requisito funcional con su historia de usuario y el microservicio responsable de implementarlo. Permite verificar que cada RF tiene cobertura en el diseño y que ningún servicio asume responsabilidades fuera de su frontera. Los requisitos y las historias están definidos en [`functional.md`](./functional.md) y [`user-stories.md`](./user-stories.md); los servicios en [`09-microservices/service-catalog.md`](../09-microservices/service-catalog.md).

## Matriz RF → HU → Servicio

| RF | Historia de usuario | Servicio responsable | Estado |
|----|---------------------|---------------------|--------|
| RF-001 | HU-01 — Gestionar estructura institucional (regionales, centros, sedes y ambientes). | `institutional-structure-service` | Documentado |
| RF-002 | HU-02 — Gestionar instructores, aprendices, coordinadores y directivos. | `actor-service` | Documentado |
| RF-003 | HU-03 — Gestionar programas de formación y diseño curricular. | `program-catalog-service` | Documentado |
| RF-004 | HU-04 — Relacionar competencias, RAP, evidencias y proyectos formativos. | `program-catalog-service` / `evidence-service` | Documentado |
| RF-005 | HU-05 — Gestionar fichas y oferta formativa. | `cohort-offering-service` | Documentado |
| RF-006 | HU-06 — Programar horarios por ficha, instructor, ambiente y periodo. | `schedule-service` | Documentado |
| RF-007 | HU-07 — Detectar conflictos de horario, ambiente e instructor. | `schedule-service` | Documentado |
| RF-008 | HU-08 — Registrar ejecución real de sesiones. | `attendance-trace-service` | Documentado |
| RF-009 | HU-09 — Registrar trazabilidad de asistencia, novedades e incidencias. | `attendance-trace-service` | Documentado |
| RF-010 | HU-10 — Gestionar proyectos formativos, entregables, hitos y dependencias. | `formative-project-service` | Documentado |
| RF-011 | HU-11 — Medir avance por aprendiz, ficha, RAP, evidencia y proyecto. | `learner-progress-service` | Documentado |
| RF-012 | HU-12 — Generar reportes y documentos PDF. | `reporting-service` | Documentado |
| RF-013 | HU-13 — Enviar notificaciones y alertas. | `notification-service` | Documentado |
| RF-014 | HU-14 — Exponer eventos para integración y auditoría. | `integration-sync-service` / `audit-compliance-service` | Documentado |
| RF-015 | HU-15 — Proveer tablero runtime de avance y desviaciones. | `reporting-service` / `learner-progress-service` | Documentado |
