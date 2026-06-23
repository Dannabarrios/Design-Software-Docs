# cohort-offering-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona fichas, oferta, proyectos formativos asociados, grupos y periodos.

## Bounded context

Oferta formativa y agrupación de aprendices. Es dueño de las fichas y la oferta. Referencia los programas (program-catalog-service) pero no los define.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| program-catalog-service | Síncrona (API) | Referencia programas y diseño curricular. |
| actor-service | Síncrona (API) | Asocia aprendices a fichas. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
