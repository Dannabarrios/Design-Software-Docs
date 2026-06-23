# data-model — actor-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Instructor | Persona que imparte y evalúa la formación. |
| Aprendiz | Persona inscrita en un programa de formación. |
| Coordinador | Persona que coordina la operación formativa. |
| Directivo | Persona con rol directivo institucional. |
| RelacionInstitucional | Vínculo de un actor con un centro o sede. |

## Relaciones

- Un `Actor` (instructor, aprendiz, coordinador, directivo) tiene una o varias `RelacionInstitucional`.
- Un `Aprendiz` se asocia a fichas a través de cohort-offering-service.
