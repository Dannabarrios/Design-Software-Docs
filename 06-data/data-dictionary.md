# Diccionario de datos

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Diccionario de las entidades principales del dominio a nivel conceptual. No describe columnas de base de datos ni tipos exactos de implementación; esos detalles están en los `data-model.md` de cada servicio en `09-microservices/services/`. Los campos listados son los atributos clave que identifican y caracterizan cada entidad.

## Entidades del dominio

### Estructura institucional

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `Regional` | `institutional-structure-service` | División territorial del SENA que agrupa centros de formación. | id, nombre, codigo |
| `CentroFormacion` | `institutional-structure-service` | Centro de formación adscrito a una regional. | id, nombre, codigo, regional_id |
| `Sede` | `institutional-structure-service` | Sede física de un centro de formación. | id, nombre, centro_id, ubicacion |
| `Ambiente` | `institutional-structure-service` | Espacio físico o virtual donde se ejecutan sesiones de formación. | id, nombre, tipo, capacidad, sede_id, estado |

### Catálogos y parametrización

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `Catalogo` | `parameter-service` | Conjunto de valores base reutilizables por otros servicios. | id, nombre, tipo |
| `Parametro` | `parameter-service` | Valor configurable del sistema. | id, clave, valor, descripcion |
| `Regla` | `parameter-service` | Regla de negocio configurable aplicable por otros servicios. | id, nombre, condicion, accion |
| `CalendarioInstitucional` | `parameter-service` | Calendario con fechas y periodos institucionales. | id, nombre, anio, fechas[] |

### Actores

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `Instructor` | `actor-service` | Persona que imparte y evalúa la formación, autorizada por competencia. | id, nombre, documento, competencias_autorizadas[], estado |
| `Aprendiz` | `actor-service` | Persona inscrita en un programa de formación. | id, nombre, documento, estado |
| `Coordinador` | `actor-service` | Persona responsable de la coordinación académica operativa. | id, nombre, documento, centro_id |
| `Directivo` | `actor-service` | Persona con rol directivo institucional. | id, nombre, documento, cargo |
| `RelacionInstitucional` | `actor-service` | Vínculo de un actor con un centro o sede. | actor_id, centro_id, rol, vigente |

### Seguridad y acceso

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `Usuario` | `auth-service` | Persona registrada con credenciales de acceso al sistema. | id, username, email, roles[], estado |
| `Rol` | `auth-service` | Agrupación de permisos asignada a uno o más usuarios. | id, nombre, permisos[] |
| `Permiso` | `auth-service` | Acción específica que puede ejecutarse sobre un recurso. | id, accion, recurso |

### Currículo y programas

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `LineaTecnologica` | `program-catalog-service` | Nivel más alto de la jerarquía curricular del SENA. | id, nombre, codigo |
| `Programa` | `program-catalog-service` | Programa de formación (titulada o complementaria) con diseño curricular oficial. | id, nombre, codigo, tipo, linea_id, estado |
| `DisenoCurricular` | `program-catalog-service` | Versión vigente del diseño curricular de un programa. | id, programa_id, version, competencias[] |
| `Competencia` | `program-catalog-service` | Unidad de competencia laboral que compone un programa de formación. | id, nombre, codigo, diseno_id |
| `RAP` | `program-catalog-service` | Resultado de Aprendizaje: unidad mínima evaluable de una competencia. | id, nombre, codigo, competencia_id |

### Oferta y fichas

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `Oferta` | `cohort-offering-service` | Apertura de un programa de formación en un periodo y centro. | id, programa_id, centro_id, periodo_id, estado |
| `Ficha` | `cohort-offering-service` | Grupo de aprendices matriculados en un programa para un periodo. | id, codigo, programa_id, periodo_id, estado |
| `Periodo` | `cohort-offering-service` | Periodo académico en el que se desarrolla la oferta. | id, nombre, fecha_inicio, fecha_fin |

### Horarios y ejecución

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `Horario` | `schedule-service` | Planificación de sesiones de formación para una ficha en un periodo. | id, ficha_id, periodo_id, estado |
| `Sesion` | `schedule-service` | Unidad de tiempo programada: fecha, bloque, instructor y ambiente. | id, horario_id, fecha, hora_inicio, hora_fin, instructor_id, ambiente_id |
| `Asignacion` | `schedule-service` | Asignación de instructor, ambiente y ficha a una sesión. | id, sesion_id, instructor_id, ambiente_id, ficha_id |
| `Conflicto` | `schedule-service` | Choque detectado de horario, ambiente o instructor. | id, tipo, sesion_ids[], descripcion |
| `EjecucionSesion` | `attendance-trace-service` | Registro de la ejecución real de una sesión programada. | id, sesion_id, fecha_ejecucion, estado |
| `Asistencia` | `attendance-trace-service` | Asistencia de un aprendiz a una sesión ejecutada. | id, ejecucion_id, aprendiz_id, presente, justificacion |
| `Novedad` | `attendance-trace-service` | Novedad registrada durante la sesión (condición especial o cambio). | id, ejecucion_id, descripcion, tipo |
| `Incidencia` | `attendance-trace-service` | Incidencia ocurrida en la ejecución (evento que afecta el normal desarrollo). | id, ejecucion_id, descripcion, severidad |

### Proyectos formativos y evidencias

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `ProyectoFormativo` | `formative-project-service` | Estrategia pedagógica que integra competencias, RAP y entregables. | id, nombre, programa_id, competencias[], estado |
| `Entregable` | `formative-project-service` | Producto esperado de un proyecto, vinculado a RAP. | id, proyecto_id, nombre, rap_id, estado |
| `Hito` | `formative-project-service` | Punto de control del avance del proyecto. | id, proyecto_id, nombre, fecha_esperada, estado |
| `Dependencia` | `formative-project-service` | Relación de dependencia entre proyectos formativos. | id, proyecto_origen_id, proyecto_dependiente_id, tipo |
| `Evidencia` | `evidence-service` | Artefacto entregado por el aprendiz como demostración del logro de un RAP. | id, aprendiz_id, rap_id, proyecto_id, estado, version_actual |
| `Version` | `evidence-service` | Versión de una evidencia entregada. | id, evidencia_id, numero, fecha_entrega, soportes[] |
| `ValidacionEvidencia` | `evidence-service` | Resultado de la validación de una evidencia por un instructor. | id, evidencia_id, instructor_id, resultado, fecha |

### Avance y seguimiento

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `AvanceAprendiz` | `learner-progress-service` | Avance consolidado de un aprendiz en su ficha, por RAP y evidencia. | id, aprendiz_id, ficha_id, porcentaje_avance, alertas[] |
| `AvanceFicha` | `learner-progress-service` | Avance consolidado del conjunto de aprendices de una ficha. | id, ficha_id, porcentaje_promedio, total_aprendices |
| `AlertaRiesgo` | `learner-progress-service` | Alerta generada por desviación o riesgo en el avance de un aprendiz. | id, aprendiz_id, tipo, descripcion, fecha |

### Coordinación y eventos

| Entidad | Servicio dueño | Descripción | Campos clave |
|---------|---------------|-------------|--------------|
| `Reporte` | `reporting-service` | Solicitud de generación de un reporte con su estado y resultado. | id, tipo, solicitante_id, estado, generado_en |
| `Indicador` | `reporting-service` | Métrica calculada del sistema (asistencia, avance, desviación). | id, nombre, valor, periodo, tablero_id |
| `Tablero` | `reporting-service` | Agrupación de indicadores presentados por rol o área. | id, nombre, rol, indicadores[] |
| `ExportablePDF` | `reporting-service` | Documento PDF generado a partir de un reporte. | id, reporte_id, url, generado_en |
| `Notificacion` | `notification-service` | Mensaje generado para uno o más destinatarios con estado de entrega. | id, plantilla_id, destinatarios[], canal_id, estado |
| `FuenteMaestra` | `integration-sync-service` | Fuente externa de datos (ej. SOFIA Plus) con configuración de conexión. | id, nombre, tipo, url, estado |
| `TrabajoSincronizacion` | `integration-sync-service` | Ejecución de un proceso de sincronización con estado y resumen. | id, fuente_id, inicio, fin, estado, registros_procesados |
| `RegistroAuditoria` | `audit-compliance-service` | Evento inmutable que registra quién hizo qué, sobre qué recurso y cuándo. | id, actor_id, accion, recurso_tipo, recurso_id, timestamp |
