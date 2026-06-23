# program-catalog-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona programas de formación, diseños curriculares, competencias, RAP y líneas tecnológicas.

## Bounded context

Dominio académico: estructura curricular del SENA. Es dueño de los programas y su diseño curricular (competencias y resultados de aprendizaje). No gestiona fichas ni oferta (eso es de cohort-offering-service) ni horarios (schedule-service).

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| parameter-service | Síncrona (API) | Consume catálogos base y tipos configurables. |
| auth-service | Síncrona (API) | Autenticación y autorización de operaciones. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para trazabilidad y auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)