# data-model — auth-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Base de datos propia del servicio. No comparte tablas con otros servicios.

## Entidades

| Entidad | Descripción |
|---------|-------------|
| Usuario | Persona registrada con credenciales de acceso al sistema. |
| Rol | Agrupación nombrada de permisos asignada a uno o más usuarios. |
| Permiso | Acción específica que puede ejecutarse sobre un recurso. |
| Sesion | Sesión activa de un usuario, con token y tiempo de expiración. |
| Token | Token JWT emitido para una sesión, con tipo (acceso/refresh) y estado. |

## Relaciones

- Un `Usuario` tiene uno o más `Rol`.
- Un `Rol` contiene muchos `Permiso`.
- Un `Usuario` puede tener muchas `Sesion` a lo largo del tiempo.
- Cada `Sesion` tiene uno o más `Token` asociados (acceso y refresh).
