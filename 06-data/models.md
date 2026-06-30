# Modelos de datos

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Visión global del modelo de datos del sistema. Los esquemas de cada dominio se documentan en `09-microservices/services/<servicio>/data-model.md`. Aquí se presenta el panorama de conjunto y el principio de organización que los rige.

> **Diferencia con `02-domain/`:** aquella sección describe las entidades en términos de negocio (invariantes, reglas, lenguaje ubicuo). Esta sección describe la implementación de persistencia.

## Principio: una base de datos, colecciones separadas por dominio

El sistema utiliza **una única base de datos MongoDB**. La separación entre dominios es lógica: cada microservicio opera sobre sus propias colecciones y nunca accede directamente a las colecciones de otro dominio. La integración entre servicios se realiza exclusivamente por API o eventos de dominio (ver [`09-microservices/communication-patterns.md`](../09-microservices/communication-patterns.md)).

Esto implica:

- Existe una sola instancia de base de datos MongoDB para todo el sistema.
- Cada microservicio tiene colecciones propias con prefijo o namespace de dominio.
- Ningún servicio consulta ni escribe en las colecciones de otro servicio.
- Las referencias a entidades de otros dominios se almacenan como identificadores planos (id), nunca como joins o referencias de base de datos cruzadas.
- Cada servicio gestiona sus propios validadores `$jsonSchema` e índices sobre sus colecciones.

## Resumen por dominio

| Servicio | Colecciones principales |
|----------|------------------------|
| `auth-service` | usuarios, roles, permisos, sesiones, tokens |
| `audit-compliance-service` | registros_auditoria, politicas_retencion |
| `parameter-service` | catalogos, parametros, reglas, calendarios_institucionales, tipos |
| `institutional-structure-service` | regionales, centros_formacion, sedes, ambientes, ubicaciones |
| `actor-service` | instructores, aprendices, coordinadores, directivos, relaciones_institucionales |
| `program-catalog-service` | lineas_tecnologicas, programas, disenos_curriculares, competencias, raps |
| `cohort-offering-service` | fichas, ofertas, grupos, periodos |
| `schedule-service` | horarios, sesiones, asignaciones, conflictos |
| `attendance-trace-service` | ejecuciones_sesion, asistencias, novedades, incidencias |
| `formative-project-service` | proyectos_formativos, dependencias, entregables, hitos |
| `evidence-service` | evidencias, versiones, soportes, validaciones_evidencia |
| `learner-progress-service` | avances_aprendiz, avances_ficha, alertas_riesgo |
| `infrastructure-service` | recursos, inventarios, disponibilidades, reservas |
| `integration-sync-service` | fuentes_maestras, trabajos_sincronizacion, registros_sincronizacion |
| `notification-service` | notificaciones, plantillas, canales_envio |
| `reporting-service` | reportes, indicadores, tableros, exportables_pdf |

## Tecnología

- **Motor:** MongoDB.
- **Instancias:** una única base de datos para todo el sistema.
- **Validación de esquema:** validadores `$jsonSchema` por colección.
- **Índices:** definidos por cada servicio sobre sus propias colecciones.
- **Consistencia:** cada servicio gestiona su propia consistencia; la consistencia entre servicios es eventual vía eventos.
