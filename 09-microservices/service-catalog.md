# Catálogo de servicios

> Estado: 🟡 En progreso | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Inventario de microservicios del sistema de horarios y trazabilidad formativa del SENA. Cada servicio tiene frontera estricta, base de datos propia y se comunica por API o eventos. Total: 16 servicios.

| Servicio | Módulo | Prioridad | Responsabilidad | Estado doc |
|----------|--------|-----------|-----------------|------------|
| auth-service | Seguridad y Acceso | P0 | Identidad, autenticación, autorización, roles y permisos. | 🔴 |
| audit-compliance-service | Seguridad y Acceso | P0 | Auditoría, retención, protección de datos y trazabilidad normativa. | 🔴 |
| parameter-service | Parametrización | P0 | Catálogos base, reglas configurables, calendarios institucionales y tipos. | 🟢 |
| institutional-structure-service | Estructura Institucional | P0 | Regionales, centros de formación, sedes, ambientes y ubicaciones. | 🟢 |
| actor-service | Actores | P0 | Instructores, aprendices, coordinadores, directivos y relaciones institucionales. | 🟢 |
| program-catalog-service | Programas de Formación | P0 | Programas, diseños curriculares, competencias, RAP y líneas tecnológicas. | 🟢 |
| cohort-offering-service | Oferta y Programas | P0 | Fichas, oferta, proyectos formativos asociados, grupos y periodos. | 🟢 |
| schedule-service | Horarios | P0 | Horarios, sesiones, asignación de instructor/ambiente/ficha y conflictos. | 🟢 |
| attendance-trace-service | Horarios | P0 | Asistencia, ejecución real de sesiones, novedades e incidencias. | 🟢 |
| formative-project-service | Proyectos Formativos | P0 | Proyectos, dependencias, entregables, hitos y conexión con diseño curricular. | 🟢 |
| evidence-service | Proyectos Formativos | P0 | Entrega, validación, versiones, soportes y relación evidencia-RAP-proyecto. | 🟢 |
| learner-progress-service | Oferta y Programas | P0 | Avance por aprendiz, ficha, RAP, evidencia, proyecto y alertas de riesgo. | 🟢 |
| infrastructure-service | Infraestructura | P1 | Ambientes, recursos, inventario base y disponibilidad de infraestructura. | 🔴 |
| integration-sync-service | Coordinación y Eventos | P1 | Sincronización con fuentes maestras externas sin reemplazar SOFIA Plus. | 🔴 |
| notification-service | Coordinación y Eventos | P1 | Mensajes, alertas, recordatorios y eventos de seguimiento. | 🔴 |
| reporting-service | Coordinación y Eventos | P1 | Indicadores, tableros, exportables, avance de fichas y trazabilidad ejecutiva. | 🔴 |