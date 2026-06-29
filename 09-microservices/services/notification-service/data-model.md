# data-model — notification-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Notificacion | Mensaje generado para uno o más destinatarios con estado de entrega. |
| Plantilla | Definición reutilizable del contenido y formato de un tipo de notificación. |
| CanalEnvio | Canal de comunicación disponible (correo electrónico, sistema interno, SMS). |

## Relaciones

- Una `Notificacion` se genera a partir de una `Plantilla`.
- Una `Notificacion` se envía por uno o más `CanalEnvio`.
- Una `Plantilla` puede originar muchas `Notificacion` a lo largo del tiempo.
