# evidence-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Gestiona la entrega, validación, versiones y soportes de evidencias, y su relación evidencia-RAP-proyecto.

## Bounded context

Evidencias del proceso formativo. Es dueño de las evidencias y sus versiones. Referencia RAP (program-catalog-service) y proyectos (formative-project-service).

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| program-catalog-service | Síncrona (API) | Relaciona evidencias con RAP. |
| formative-project-service | Síncrona (API) | Relaciona evidencias con proyectos. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
