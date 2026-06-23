# data-model — cohort-offering-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Ficha | Grupo de aprendices asociado a un programa y periodo. |
| Oferta | Oferta formativa disponible. |
| Grupo | Agrupación de aprendices dentro de una ficha. |
| Periodo | Periodo académico de la oferta. |

## Relaciones

- Una `Oferta` genera muchas `Ficha`.
- Una `Ficha` pertenece a un `Periodo`.
- Una `Ficha` referencia un programa de program-catalog-service.
