# data-model — formative-project-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| ProyectoFormativo | Estrategia que integra competencias y RAP. |
| Dependencia | Relación de dependencia entre proyectos. |
| Entregable | Producto esperado de un proyecto. |
| Hito | Punto de control del avance del proyecto. |

## Relaciones

- Un `ProyectoFormativo` tiene muchos `Entregable` y `Hito`.
- Un `ProyectoFormativo` puede tener `Dependencia` con otros proyectos.
