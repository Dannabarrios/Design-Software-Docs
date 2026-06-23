# data-model — attendance-trace-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| EjecucionSesion | Registro de la ejecución real de una sesión. |
| Asistencia | Asistencia de un aprendiz a una sesión. |
| Novedad | Novedad registrada durante la sesión. |
| Incidencia | Incidencia ocurrida en la ejecución. |

## Relaciones

- Una `EjecucionSesion` referencia una sesión de schedule-service.
- Una `EjecucionSesion` tiene muchas `Asistencia`.
- Una `EjecucionSesion` puede tener `Novedad` e `Incidencia`.
