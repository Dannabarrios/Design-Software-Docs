# infrastructure-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona recursos, inventario base y disponibilidad de ambientes físicos del SENA.

## Bounded context

Dominio de infraestructura física. Es dueño de los ambientes (laboratorios, aulas, talleres), sus recursos asociados y la disponibilidad operativa de cada uno. No gestiona horarios (schedule-service); informa disponibilidad para que schedule-service la consulte.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| auth-service | Síncrona (API) | Autenticación y autorización de operaciones. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos de cambios de inventario y disponibilidad para trazabilidad. |
| schedule-service | Asíncrona (evento) | Consume eventos de sesión para actualizar disponibilidad de ambientes. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
