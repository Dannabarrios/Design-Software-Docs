# data-model — learner-progress-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| AvanceAprendiz | Avance consolidado de un aprendiz. |
| AvanceFicha | Avance consolidado de una ficha. |
| AlertaRiesgo | Alerta generada por desviación o riesgo. |

## Relaciones

- Un `AvanceFicha` agrega muchos `AvanceAprendiz`.
- Un `AvanceAprendiz` puede generar una `AlertaRiesgo`.
