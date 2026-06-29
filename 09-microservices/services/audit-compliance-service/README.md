# audit-compliance-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Registra de forma append-only todas las acciones de auditoría del sistema, gestiona políticas de retención y garantiza la trazabilidad normativa y protección de datos.

## Bounded context

Dominio de cumplimiento y auditoría. Es dueño de los registros de auditoría inmutables del sistema. No gestiona identidades (auth-service) ni datos operativos de otros dominios. Solo acepta inserciones; los registros nunca se actualizan ni eliminan antes de cumplir la política de retención.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| auth-service | Asíncrona (evento) | Consume eventos de autenticación para registrar accesos. |
| Todos los servicios de dominio | Asíncrona (evento) | Consume eventos de cambio para construir el log de auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
