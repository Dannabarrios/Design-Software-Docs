# Roadmap

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Evolución planificada del producto por fases. La priorización sigue el catálogo de servicios definido en [`09-microservices/service-catalog.md`](../09-microservices/service-catalog.md): primero los servicios núcleo del dominio (P0), luego los servicios de infraestructura, integración y coordinación (P1).

## Fases

| Fase | Objetivo | Servicios / Entregables |
|------|----------|------------------------|
| **Fase 1 — Núcleo del dominio (P0)** | Habilitar el ciclo completo de planificación, ejecución y trazabilidad formativa. | `auth-service`, `audit-compliance-service`, `parameter-service`, `institutional-structure-service`, `actor-service`, `program-catalog-service`, `cohort-offering-service`, `schedule-service`, `attendance-trace-service`, `formative-project-service`, `evidence-service`, `learner-progress-service` |
| **Fase 2 — Coordinación y extensión (P1)** | Habilitar infraestructura física, integración con fuentes maestras, notificaciones y reportes ejecutivos. | `infrastructure-service`, `integration-sync-service`, `notification-service`, `reporting-service` |

## Detalle por fase

### Fase 1 — Núcleo del dominio (P0)

Construye las capacidades esenciales sin las cuales el sistema no puede operar: identidad y acceso, estructura institucional, actores, currículo, fichas, horarios, ejecución de sesiones, evidencias y avance del aprendiz.

| Entregable | Servicio | Capacidad habilitada |
|-----------|---------|----------------------|
| Autenticación y autorización | `auth-service` | Acceso seguro al sistema con roles y permisos. |
| Auditoría y cumplimiento | `audit-compliance-service` | Trazabilidad normativa de acciones del sistema. |
| Catálogos base | `parameter-service` | Catálogos, calendarios y tipos configurables. |
| Estructura institucional | `institutional-structure-service` | Regionales, centros, sedes y ambientes. |
| Gestión de actores | `actor-service` | Instructores, aprendices, coordinadores y directivos. |
| Catálogo de programas | `program-catalog-service` | Programas, diseño curricular, competencias y RAP. |
| Fichas y oferta | `cohort-offering-service` | Grupos, periodos y oferta formativa. |
| Horarios | `schedule-service` | Planificación de sesiones y detección de conflictos. |
| Ejecución y trazabilidad | `attendance-trace-service` | Registro de ejecución real, asistencia y novedades. |
| Proyectos formativos | `formative-project-service` | Proyectos, entregables, hitos y dependencias. |
| Evidencias | `evidence-service` | Entrega, validación y relación evidencia-RAP. |
| Avance del aprendiz | `learner-progress-service` | Medición de avance por aprendiz, ficha y RAP. |

### Fase 2 — Coordinación y extensión (P1)

Amplía el sistema con gestión de recursos físicos, sincronización con fuentes maestras externas, alertas y reportes ejecutivos.

| Entregable | Servicio | Capacidad habilitada |
|-----------|---------|----------------------|
| Gestión de infraestructura | `infrastructure-service` | Inventario de ambientes, recursos y disponibilidad. |
| Integración con fuentes maestras | `integration-sync-service` | Sincronización con SOFIA Plus y otras fuentes sin reemplazarlas. |
| Notificaciones y alertas | `notification-service` | Mensajes, recordatorios y alertas de seguimiento. |
| Reportes y exportables | `reporting-service` | Tableros, indicadores, actas y PDF auditables. |
