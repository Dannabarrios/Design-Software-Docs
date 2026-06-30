# Vista general de arquitectura

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

## Estilo arquitectónico

El sistema se construye bajo una **arquitectura de microservicios** con fronteras estrictas por dominio (ADR-0001). Cada microservicio es dueño de su dominio y se comunica con los demás exclusivamente por API REST o eventos de dominio; ningún servicio accede a las colecciones internas de otro. El sistema no reemplaza a SOFIA Plus ni crea una fuente maestra institucional paralela (ADR-0002).

## Agrupación de servicios por módulo

Los 16 servicios se agrupan en dos categorías: **servicios de dominio SENA** (responsables de la lógica formativa y operativa) y **servicios transversales** (seguridad, auditoría, parametrización, integración, notificación y reportes).

### Servicios de dominio SENA

| Módulo | Servicio | Responsabilidad |
|--------|----------|-----------------|
| Estructura Institucional | `institutional-structure-service` | Regionales, centros, sedes y ambientes. |
| Actores | `actor-service` | Instructores, aprendices, coordinadores y directivos. |
| Programas de Formación | `program-catalog-service` | Programas, diseño curricular, competencias y RAP. |
| Oferta y Programas | `cohort-offering-service` | Fichas, oferta, grupos y periodos. |
| Oferta y Programas | `learner-progress-service` | Avance por aprendiz, ficha, RAP, evidencia y alertas. |
| Horarios | `schedule-service` | Planificación de sesiones y detección de conflictos. |
| Horarios | `attendance-trace-service` | Ejecución real de sesiones, asistencia y novedades. |
| Proyectos Formativos | `formative-project-service` | Proyectos, entregables, hitos y dependencias. |
| Proyectos Formativos | `evidence-service` | Entrega, validación y relación evidencia-RAP. |
| Infraestructura | `infrastructure-service` | Recursos físicos, inventario y disponibilidad. |

### Servicios transversales

| Módulo | Servicio | Responsabilidad |
|--------|----------|-----------------|
| Seguridad y Acceso | `auth-service` | Identidad, autenticación, autorización y tokens. |
| Seguridad y Acceso | `audit-compliance-service` | Auditoría, retención y protección de datos. |
| Parametrización | `parameter-service` | Catálogos base, reglas y calendarios institucionales. |
| Coordinación y Eventos | `integration-sync-service` | Sincronización con fuentes maestras externas. |
| Coordinación y Eventos | `notification-service` | Mensajes, alertas y recordatorios. |
| Coordinación y Eventos | `reporting-service` | Indicadores, tableros y exportables PDF. |

## Comunicación entre servicios

La comunicación entre servicios sigue dos patrones complementarios (ver [`communication-patterns.md`](../09-microservices/communication-patterns.md)):

| Patrón | Cuándo se usa | Ejemplo |
|--------|--------------|---------|
| **Síncrono (REST)** | Operaciones que requieren respuesta inmediata. | Consultar fichas de `cohort-offering-service` desde `schedule-service`. |
| **Asíncrono (eventos)** | Notificar cambios de estado sin esperar respuesta. | `SchedulePlanned` publicado por `schedule-service`, consumido por `notification-service`. |

Todas las llamadas propagan `correlation_id` en el encabezado `X-Correlation-ID` (RNF-004). El acceso a datos de otro servicio siempre es por contrato de API, nunca por acceso directo a colecciones.

## Decisiones de arquitectura

| ADR | Decisión |
|-----|----------|
| [ADR-0001](./decisions/records/ADR-001-arquitectura-microservicios.md) | Arquitectura basada en microservicios con una única base de datos MongoDB y colecciones separadas por dominio. |
| [ADR-0002](./decisions/records/ADR-002-no-reemplazo-sofia-plus.md) | El sistema no reemplaza a SOFIA Plus; se integra con fuentes maestras sin ser fuente maestra. |
