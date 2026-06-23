# data-model — program-catalog-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| LineaTecnologica | Línea tecnológica que agrupa programas. |
| Programa | Programa de formación (titulada, complementaria, etc.). |
| DisenoCurricular | Diseño curricular asociado a un programa. |
| Competencia | Competencia del diseño curricular. |
| RAP | Resultado de Aprendizaje asociado a una competencia. |

## Relaciones

- Una `LineaTecnologica` agrupa muchos `Programa`.
- Un `Programa` tiene un `DisenoCurricular`.
- Un `DisenoCurricular` contiene muchas `Competencia`.
- Una `Competencia` contiene muchos `RAP`.