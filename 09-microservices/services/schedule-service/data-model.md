# data-model — schedule-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Horario | Programación temporal de una ficha. |
| Sesion | Sesión de formación programada. |
| Asignacion | Asignación de instructor, ambiente y ficha a una sesión. |
| Conflicto | Choque detectado de horario, ambiente o instructor. |

## Relaciones

- Un `Horario` contiene muchas `Sesion`.
- Una `Sesion` tiene una `Asignacion`.
- Una `Asignacion` puede generar uno o varios `Conflicto`.
