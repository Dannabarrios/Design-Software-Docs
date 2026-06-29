# Mapa de dominio

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Descripción de los bounded contexts del sistema de horarios y trazabilidad formativa del SENA. Cada contexto agrupa servicios con responsabilidad cohesionada y frontera estricta; ningún servicio accede a datos internos de otro contexto.

## Bounded contexts

### Seguridad y Acceso

Controla la identidad de los usuarios, el acceso al sistema y la trazabilidad normativa.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `auth-service` | Autenticación, autorización, roles y permisos. |
| `audit-compliance-service` | Auditoría de acciones, retención y protección de datos. |

---

### Estructura Institucional

Modela la jerarquía física y organizativa del SENA: regionales, centros, sedes y ambientes.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `institutional-structure-service` | Regionales, centros de formación, sedes, ambientes y ubicaciones. |

---

### Parametrización

Centraliza los catálogos base y reglas configurables que los demás contextos consumen.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `parameter-service` | Catálogos base, reglas configurables, calendarios institucionales y tipos. |

---

### Programas de Formación

Modela la estructura curricular oficial: desde la línea tecnológica hasta el RAP.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `program-catalog-service` | Programas, diseños curriculares, competencias, RAP y líneas tecnológicas. |

---

### Oferta y Programas

Gestiona la oferta formativa concreta: fichas abiertas, grupos y el avance de cada aprendiz.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `cohort-offering-service` | Fichas, oferta, grupos, periodos y proyectos formativos asociados. |
| `learner-progress-service` | Avance por aprendiz, ficha, RAP, evidencia y alertas de riesgo. |

---

### Actores

Agrupa a todos los actores humanos del sistema y sus relaciones con la institución.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `actor-service` | Instructores, aprendices, coordinadores, directivos y relaciones institucionales. |

---

### Horarios

Controla la planificación de sesiones y el registro real de lo ejecutado.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `schedule-service` | Horarios, sesiones, asignación instructor/ambiente/ficha y detección de conflictos. |
| `attendance-trace-service` | Asistencia, ejecución real de sesiones, novedades e incidencias. |

---

### Proyectos Formativos

Gestiona los proyectos de aprendizaje vinculados al diseño curricular, sus entregables y las evidencias de los aprendices.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `formative-project-service` | Proyectos, dependencias, entregables, hitos y conexión con diseño curricular. |
| `evidence-service` | Entrega, validación, versiones, soportes y relación evidencia-RAP-proyecto. |

---

### Infraestructura

Administra los recursos físicos y la disponibilidad de ambientes de formación.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `infrastructure-service` | Ambientes, recursos, inventario base y disponibilidad de infraestructura. |

---

### Coordinación y Eventos

Servicios transversales de integración, notificación y reporte que no pertenecen a un dominio funcional único.

| Servicio | Responsabilidad principal |
|----------|--------------------------|
| `integration-sync-service` | Sincronización con fuentes maestras externas sin reemplazar SOFIA Plus. |
| `notification-service` | Mensajes, alertas, recordatorios y eventos de seguimiento. |
| `reporting-service` | Indicadores, tableros, exportables, avance de fichas y trazabilidad ejecutiva. |

---

## Relaciones entre contextos

| Contexto origen | Contexto destino | Tipo de relación |
|-----------------|-----------------|-----------------|
| Horarios | Estructura Institucional | Consume datos de ambientes por API. |
| Horarios | Actores | Consume datos de instructores por API. |
| Horarios | Oferta y Programas | Consume datos de fichas por API. |
| Proyectos Formativos | Programas de Formación | Consume competencias y RAP por API. |
| Oferta y Programas | Programas de Formación | Consume diseño curricular por API. |
| Coordinación y Eventos | Todos | Consume eventos de dominio publicados por los demás contextos. |
| Seguridad y Acceso | Todos | Provee tokens de autorización y registra auditoría transversalmente. |
