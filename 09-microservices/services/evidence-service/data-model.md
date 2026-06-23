# data-model — evidence-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Evidencia | Soporte que demuestra el logro de un RAP. |
| Version | Versión de una evidencia entregada. |
| Soporte | Archivo o documento asociado a la evidencia. |
| ValidacionEvidencia | Resultado de la validación de una evidencia. |

## Relaciones

- Una `Evidencia` tiene muchas `Version`.
- Una `Version` tiene uno o varios `Soporte`.
- Una `Evidencia` tiene una `ValidacionEvidencia` al ser validada.
