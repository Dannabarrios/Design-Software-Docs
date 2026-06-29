# data-model — reporting-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Reporte | Solicitud de generación de un reporte con su estado y resultado. |
| Indicador | Métrica calculada del sistema (p. ej. porcentaje de asistencia, avance de ficha). |
| Tablero | Agrupación de indicadores presentados por rol o área. |
| ExportablePDF | Documento PDF generado a partir de un reporte aprobado. |

## Relaciones

- Un `Tablero` contiene muchos `Indicador`.
- Un `Reporte` puede generar uno o más `ExportablePDF`.
- Un `Indicador` es calculado a partir de eventos consolidados de múltiples servicios.
