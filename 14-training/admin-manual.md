# Manual del administrador

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Guía para administradores del sistema de horarios y trazabilidad formativa del SENA. Cubre las tareas de configuración, gestión de estructura institucional, actores, programas, oferta y parámetros del sistema.

> Este manual describe las funciones administrativas disponibles. Los flujos detallados de interfaz de usuario se documentarán en [`12-ux-ui/`](../12-ux-ui/) cuando estén definidos.

---

## Gestión de estructura institucional

Administrar la jerarquía física y organizativa del SENA: regionales, centros de formación, sedes y ambientes. Corresponde a las funciones de `institutional-structure-service` (RF-001).

| Tarea | Descripción |
|-------|-------------|
| Registrar regional | Crear o actualizar una regional del SENA. |
| Registrar centro de formación | Asociar un centro a una regional. |
| Registrar sede | Asociar una sede física a un centro de formación. |
| Registrar ambiente | Crear un espacio de formación (aula, laboratorio, taller) dentro de una sede, con capacidad y tipo. |
| Actualizar disponibilidad de ambiente | Marcar un ambiente como disponible, en mantenimiento o fuera de servicio. |

---

## Gestión de actores

Administrar los actores del proceso formativo: instructores, aprendices, coordinadores y directivos. Corresponde a `actor-service` (RF-002).

| Tarea | Descripción |
|-------|-------------|
| Registrar instructor | Crear el perfil de un instructor con sus competencias autorizadas. |
| Registrar aprendiz | Crear el perfil de un aprendiz en el sistema. |
| Registrar coordinador o directivo | Crear el perfil de un coordinador o directivo con su vínculo institucional. |
| Actualizar relación institucional | Asociar o desasociar un actor de un centro o sede. |
| Actualizar competencias autorizadas de un instructor | Modificar las competencias para las que un instructor está habilitado. |

---

## Gestión de programas y diseño curricular

Administrar la estructura curricular: programas de formación, diseños curriculares, competencias y RAP. Corresponde a `program-catalog-service` (RF-003, RF-004).

| Tarea | Descripción |
|-------|-------------|
| Registrar programa de formación | Crear un programa (titulado o complementario) con su línea tecnológica. |
| Registrar diseño curricular | Asociar un diseño curricular a un programa. |
| Registrar competencia | Agregar una competencia a un diseño curricular. |
| Registrar RAP | Agregar un Resultado de Aprendizaje a una competencia. |
| Relacionar evidencias y proyectos formativos con RAP | Vincular las estrategias de evaluación al diseño curricular. |

---

## Gestión de fichas y oferta formativa

Administrar la oferta formativa concreta: fichas abiertas, grupos y periodos. Corresponde a `cohort-offering-service` (RF-005).

| Tarea | Descripción |
|-------|-------------|
| Registrar oferta | Abrir una oferta formativa para un programa en un periodo y centro. |
| Registrar ficha | Crear un grupo de aprendices asociado a una oferta. |
| Registrar periodo | Definir las fechas de inicio y fin de un periodo académico. |
| Asociar aprendices a una ficha | Vincular aprendices a una ficha activa. |

---

## Gestión de parámetros y catálogos

Administrar los catálogos base, reglas configurables y calendarios institucionales. Corresponde a `parameter-service`.

| Tarea | Descripción |
|-------|-------------|
| Gestionar catálogos | Crear y actualizar conjuntos de valores base reutilizables (tipos, estados, categorías). |
| Gestionar parámetros del sistema | Configurar valores que controlan el comportamiento del sistema. |
| Gestionar reglas | Definir reglas de negocio configurables aplicables por otros servicios. |
| Gestionar calendario institucional | Registrar fechas especiales, festivos y periodos de la institución. |

---

## Gestión de roles y permisos

Administrar el modelo de acceso al sistema: usuarios, roles y permisos. Corresponde a `auth-service` (RNF-001).

| Tarea | Descripción |
|-------|-------------|
| Crear usuario | Registrar un nuevo usuario con credenciales de acceso. |
| Asignar rol | Asociar uno o más roles a un usuario. |
| Gestionar roles | Crear o modificar roles y los permisos que agrupan. |
| Revocar acceso | Desactivar un usuario o modificar sus roles. |
| Revisar registro de auditoría | Consultar el historial de acciones sensibles en `audit-compliance-service`. |
