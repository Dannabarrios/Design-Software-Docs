# formative-project-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona proyectos formativos, dependencias, entregables, hitos y su conexión con el diseño curricular.

## Bounded context

Proyectos formativos como estrategia pedagógica. Es dueño de proyectos, entregables e hitos. Referencia el diseño curricular de program-catalog-service.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| program-catalog-service | Síncrona (API) | Conecta proyectos con competencias y RAP. |
| cohort-offering-service | Síncrona (API) | Referencia fichas asociadas. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
