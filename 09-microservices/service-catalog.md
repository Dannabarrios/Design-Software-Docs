# Catálogo de servicios

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Inventario de microservicios del sistema. Cada servicio tiene frontera estricta, base de datos propia y se comunica por API o eventos. Total: 28 servicios.

| Servicio | Módulo | Prioridad | Responsabilidad | Estado doc |
|----------|--------|-----------|-----------------|------------|
| auth-service | Seguridad y Acceso | P0 | Identidad, autenticación, autorización, roles, permisos y auditoría de acceso. | 🔴 |
| control-plane-service | Seguridad y Acceso | P0 | Registro de proyectos, runs, agentes, políticas, costos y gobierno operacional del ecosistema. | 🔴 |
| workflow-service | Coordinación y Eventos | P0 | Orquestación de procesos de negocio y estados de ejecución formativa. | 🔴 |
| run-state-service | Infraestructura | P0 | Estado de ejecución de agentes, checkpoints, reanudación y trazabilidad operacional. | 🔴 |
| tool-gateway-service | Infraestructura | P0 | Frontera de herramientas, MCP, permisos, auditoría y ejecución segura. | 🔴 |
| pdf-worker-service | Infraestructura | P0 | Generación asincrónica de documentos PDF, reportes, actas y soportes. | 🔴 |
| artifact-store-service | Infraestructura | P0 | Gestión de artefactos, evidencias, documentos, versiones y metadatos. | 🔴 |
| memory-service | Infraestructura | P0 | Memoria de contexto, recuperación semántica y referencias del ecosistema. | 🔴 |
| scheduler-service | Horarios | P0 | Planificación temporal, jobs, calendarios, disponibilidad y conflictos. | 🔴 |
| observability-service | Infraestructura | P0 | Trazas, métricas, logs, tool calls, costos, tokens y dashboards. | 🔴 |
| secrets-vault-service | Seguridad y Acceso | P0 | Custodia de secretos, llaves, tokens, credenciales e inyección segura. | 🔴 |
| model-router-service | Infraestructura | P0 | Enrutamiento de modelos IA por costo, capacidad, latencia, proveedor y riesgo. | 🔴 |
| eval-lab-service | Infraestructura | P0 | Evaluaciones, golden tasks, regresiones, scorecards y bloqueo por calidad. | 🔴 |
| actor-service | Actores | P0 | Instructores, aprendices, coordinadores, directivos y relaciones institucionales. | 🔴 |
| institutional-structure-service | Estructura Institucional | P0 | Regionales, centros de formación, sedes, ambientes y ubicaciones. | 🔴 |
| infrastructure-service | Infraestructura | P1 | Ambientes, recursos, inventario base y disponibilidad de infraestructura. | 🔴 |
| parameter-service | Parametrización | P0 | Catálogos base, reglas configurables, calendarios institucionales y tipos. | 🔴 |
| program-catalog-service | Programas de Formación | P0 | Programas, diseños curriculares, competencias, RAP y líneas tecnológicas. | 🔴 |
| cohort-offering-service | Oferta y Programas | P0 | Fichas, oferta, proyectos formativos asociados, grupos y periodos. | 🔴 |
| schedule-service | Horarios | P0 | Horarios, sesiones, asignación de instructor/ambiente/ficha y conflictos. | 🔴 |
| attendance-trace-service | Horarios | P0 | Asistencia, ejecución real de sesiones, novedades e incidencias runtime. | 🔴 |
| formative-project-service | Proyectos Formativos | P0 | Proyectos, dependencias, entregables, hitos, conexión con diseño curricular. | 🔴 |
| learner-progress-service | Oferta y Programas | P0 | Avance por aprendiz, ficha, RAP, evidencia, proyecto y alertas de riesgo. | 🔴 |
| evidence-service | Proyectos Formativos | P0 | Entrega, validación, versiones, soportes y relación evidencia-RAP-proyecto. | 🔴 |
| integration-sync-service | Coordinación y Eventos | P1 | Sincronización con fuentes maestras externas sin reemplazar SOFIA Plus. | 🔴 |
| notification-service | Coordinación y Eventos | P1 | Mensajes, alertas, recordatorios y eventos de seguimiento. | 🔴 |
| reporting-service | Coordinación y Eventos | P1 | Indicadores, tableros, exportables, avance de fichas y trazabilidad ejecutiva. | 🔴 |
| audit-compliance-service | Seguridad y Acceso | P0 | Auditoría, retención, protección de datos, trazabilidad normativa y evidencias de cumplimiento. | 🔴 |