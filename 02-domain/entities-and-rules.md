# Entidades y reglas de negocio

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Modelo de dominio en términos de negocio. No describe tablas ni esquemas de base de datos; esos detalles pertenecen a [`06-data/`](../06-data/).

## Entidades principales

| Entidad | Servicio dueño | Descripción |
|---------|---------------|-------------|
| `LineaTecnologica` | `program-catalog-service` | Nivel más alto de la jerarquía curricular del SENA. |
| `RedTecnologica` | `program-catalog-service` | Agrupa redes de conocimiento afines dentro de una línea tecnológica. |
| `RedConocimiento` | `program-catalog-service` | Agrupa programas de formación dentro de una red tecnológica. |
| `ProgramaFormacion` | `program-catalog-service` | Programa de formación titulada o complementaria con diseño curricular oficial. |
| `DisenioCurricular` | `program-catalog-service` | Versión vigente del diseño curricular de un programa. |
| `Competencia` | `program-catalog-service` | Unidad de competencia laboral que compone un programa de formación. |
| `RAP` | `program-catalog-service` | Resultado de Aprendizaje, unidad mínima evaluable de una competencia. |
| `Regional` | `institutional-structure-service` | División territorial del SENA. |
| `CentroFormacion` | `institutional-structure-service` | Centro de formación adscrito a una regional. |
| `Sede` | `institutional-structure-service` | Sede física de un centro de formación. |
| `Ambiente` | `institutional-structure-service` | Espacio físico o virtual donde se ejecutan sesiones de formación. |
| `Instructor` | `actor-service` | Profesional autorizado para impartir formación en competencias específicas. |
| `Aprendiz` | `actor-service` | Persona matriculada en una ficha de formación. |
| `Coordinador` | `actor-service` | Actor institucional responsable de la coordinación académica. |
| `Ficha` | `cohort-offering-service` | Grupo de aprendices matriculados en un programa de formación en un periodo. |
| `Oferta` | `cohort-offering-service` | Apertura de un programa de formación en un periodo y centro determinados. |
| `Horario` | `schedule-service` | Planificación de sesiones de formación para una ficha en un ambiente. |
| `Sesion` | `schedule-service` | Unidad de tiempo programada dentro de un horario (fecha, hora, instructor, ambiente). |
| `RegistroAsistencia` | `attendance-trace-service` | Registro real de ejecución de una sesión: asistencia, novedades e incidencias. |
| `ProyectoFormativo` | `formative-project-service` | Proyecto de aprendizaje vinculado a un programa, competencias y RAP. |
| `Entregable` | `formative-project-service` | Producto o artefacto que el aprendiz debe entregar como parte de un proyecto. |
| `Evidencia` | `evidence-service` | Artefacto concreto entregado por el aprendiz, vinculado a un RAP y proyecto. |
| `AvanceAprendiz` | `learner-progress-service` | Estado de avance de un aprendiz en su ficha, por RAP y evidencia. |
| `Rol` | `auth-service` | Conjunto de permisos asignado a un usuario en el sistema. |
| `RegistroAuditoria` | `audit-compliance-service` | Traza inmutable de una acción realizada en el sistema. |

## Reglas de negocio

### Jerarquía curricular

La estructura curricular del SENA sigue una jerarquía estricta de mayor a menor granularidad:

```
Línea Tecnológica → Red Tecnológica → Red de Conocimiento
  → Programa de Formación → Competencia → RAP
```

Un RAP pertenece a exactamente una Competencia; una Competencia pertenece a exactamente un Programa de Formación. No se pueden crear RAP sin Competencia ni Competencias sin Programa.

### Aislamiento de datos por servicio

Cada servicio es el único dueño de su base de datos. Ningún otro servicio puede acceder directamente a sus tablas. La integración entre servicios se realiza exclusivamente por API o eventos de dominio.

### Prioridad en asignación de horarios

Cuando un mismo ambiente tiene solicitudes concurrentes de asignación, la formación titulada (fichas de programas con diseño curricular oficial) tiene prioridad sobre la formación complementaria (cursos a la medida) para ese ambiente en el mismo bloque horario.

### Formación titulada y modalidad "a la medida"

Un programa de formación titulada nunca puede clasificarse ni operarse como formación "a la medida". La distinción entre formación titulada y complementaria es un atributo de diseño del programa, no de la ejecución.

### Autorización de instructores

Un instructor es autorizado para impartir formación a nivel de Competencia completa, no a nivel de RAP individual. La autorización cubre todos los RAP de la Competencia para la que fue habilitado.
