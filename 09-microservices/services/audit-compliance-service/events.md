# events — audit-compliance-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `AuditLogCreated` | Se inserta un nuevo registro de auditoría. |
| `RetentionPolicyApplied` | Una política de retención se ejecuta sobre registros vencidos. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| `UserAuthenticated` | auth-service | Registra accesos al sistema en el log de auditoría. |
| `UserLoggedOut` | auth-service | Registra cierre de sesión en el log de auditoría. |
| `RoleAssigned` | auth-service | Registra cambios de roles para trazabilidad normativa. |
| Cualquier evento de cambio de dominio | Servicios de dominio | Construye el historial inmutable de modificaciones del sistema. |
