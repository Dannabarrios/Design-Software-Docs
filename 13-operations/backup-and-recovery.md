# Respaldo y recuperación

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Lineamientos de respaldo y recuperación de datos del sistema. La estrategia parte de la separación de colecciones por dominio dentro de una única base de datos MongoDB, donde cada microservicio opera exclusivamente sobre sus propias colecciones.

## Principios

- Cada dominio (microservicio) es responsable de definir sus necesidades de respaldo según la criticidad de sus datos.
- Los datos maestros provenientes de fuentes externas (fichas, aprendices, instructores, programas sincronizados vía `integration-sync-service`) no se respaldan como datos propietarios del sistema; ante un fallo, se re-sincronizan desde la fuente maestra autorizada.
- Los datos operativos generados por el sistema (horarios, ejecución de sesiones, asistencia, evidencias, avances, registros de auditoría) sí son propietarios y deben respaldarse.
- El registro de auditoría de `audit-compliance-service` es append-only e inmutable; su respaldo tiene prioridad máxima.

## Datos propietarios que se respaldan

| Dominio | Servicio | Datos críticos |
|---------|----------|----------------|
| Seguridad y auditoría | `auth-service`, `audit-compliance-service` | Usuarios, roles, permisos, registros de auditoría. |
| Horarios | `schedule-service`, `attendance-trace-service` | Horarios planificados, ejecuciones de sesión, asistencia, novedades. |
| Proyectos y evidencias | `formative-project-service`, `evidence-service` | Proyectos, entregables, hitos, evidencias entregadas y validadas. |
| Avance | `learner-progress-service` | Avance de aprendices, fichas y alertas de riesgo. |
| Reportes | `reporting-service` | Reportes generados y exportables PDF. |

## Datos que se re-sincronizan (no se respaldan como propietario)

Los datos maestros institucionales no son propiedad del sistema. Ante un fallo que los afecte, la recuperación se realiza re-ejecutando la sincronización desde la fuente maestra a través de `integration-sync-service`:

- Fichas y oferta formativa.
- Aprendices e instructores.
- Programas de formación, competencias y RAP.

## Retención de respaldos

La política de retención de respaldos está pendiente de definición. Ver [`15-project-control/open-questions.md`](../15-project-control/open-questions.md) Q-05 (política de retención documental para evidencias, reportes y actas). Hasta que Q-05 esté resuelta, la retención no debe implementarse con supuestos no validados.

## Recuperación ante fallos

### Fallo de un servicio (sin pérdida de datos)

1. Verificar el estado del servicio con `GET /health`.
2. Reiniciar el contenedor del servicio afectado.
3. Confirmar que el servicio recupera la conexión a MongoDB y responde correctamente.
4. Revisar los eventos pendientes de procesamiento y reprocessar si aplica.

### Fallo de la base de datos MongoDB

1. Detener todos los servicios para evitar escrituras inconsistentes durante la recuperación.
2. Restaurar desde el respaldo más reciente disponible.
3. Verificar la integridad de las colecciones críticas (auditoría, horarios, evidencias).
4. Reactivar los servicios en orden: primero `auth-service` y `audit-compliance-service`, luego los demás.
5. Re-sincronizar los datos maestros externos mediante `integration-sync-service` si fueron afectados.

### Pérdida parcial de datos operativos

- Los datos de auditoría (`audit-compliance-service`) son prioritarios; ante cualquier inconsistencia, se investiga antes de continuar la operación.
- Los datos de avance (`learner-progress-service`) pueden recalcularse a partir de evidencias y asistencias si el respaldo no está disponible.

## Consideraciones pendientes

Los objetivos de punto de recuperación (RPO) y tiempo de recuperación (RTO) no están definidos. Ver [`15-project-control/open-questions.md`](../15-project-control/open-questions.md) Q-15 (SLA esperado por coordinación para carga de horarios, trazas y reportes).
