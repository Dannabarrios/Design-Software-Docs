# schedule-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona horarios, sesiones y la asignación de instructor, ambiente y ficha, detectando conflictos.

## Bounded context

Programación temporal de la formación. Es dueño de los horarios y asignaciones. La ejecución real de las sesiones es de attendance-trace-service.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| cohort-offering-service | Síncrona (API) | Referencia fichas a programar. |
| actor-service | Síncrona (API) | Referencia instructores a asignar. |
| institutional-structure-service | Síncrona (API) | Referencia ambientes a asignar. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
