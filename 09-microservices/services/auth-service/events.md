# events — auth-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `UserAuthenticated` | Un usuario inicia sesión correctamente. |
| `UserLoggedOut` | Un usuario cierra su sesión. |
| `UserCreated` | Se registra un nuevo usuario en el sistema. |
| `RoleAssigned` | Se asigna un rol a un usuario. |
| `PermissionGranted` | Se otorga un permiso a un rol. |
| `TokenRevoked` | Un token es invalidado antes de su expiración. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| — | — | El servicio no consume eventos en esta versión. |
