# data-model — institutional-structure-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Regional | Agrupación territorial de centros. |
| CentroFormacion | Centro de formación adscrito a una regional. |
| Sede | Sede física de un centro. |
| Ambiente | Espacio donde se desarrolla la formación. |
| Ubicacion | Datos de ubicación de una sede o ambiente. |

## Relaciones

- Una `Regional` agrupa muchos `CentroFormacion`.
- Un `CentroFormacion` tiene muchas `Sede`.
- Una `Sede` contiene muchos `Ambiente`.
