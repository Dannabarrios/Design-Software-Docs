# data-model — integration-sync-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| FuenteMaestra | Fuente externa de datos (p. ej. SOFIA Plus) con su configuración de conexión. |
| TrabajoSincronizacion | Ejecución de un proceso de sincronización con estado y resumen de resultados. |
| RegistroSincronizacion | Detalle de cada registro procesado durante un trabajo de sincronización. |

## Relaciones

- Una `FuenteMaestra` origina muchos `TrabajoSincronizacion`.
- Un `TrabajoSincronizacion` produce muchos `RegistroSincronizacion`.
