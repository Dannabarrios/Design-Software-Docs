# learner-progress-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

## Responsabilidad

Mide el avance por aprendiz, ficha, RAP, evidencia y proyecto, y genera alertas de riesgo.

## Bounded context

Avance en tiempo de ejecución. Consolida información de otros servicios para medir progreso; no es dueño de las evidencias ni de las fichas, las referencia.

## Dependencias

| Servicio | Tipo | Motivo |
|----------|------|--------|
| evidence-service | Asíncrona (evento) | Actualiza avance al validarse evidencias. |
| cohort-offering-service | Síncrona (API) | Referencia fichas y aprendices. |
| audit-compliance-service | Asíncrona (evento) | Publica eventos para auditoría. |

## Links

- Repo:
- API Contract: [api-contract.md](./api-contract.md)
- Data Model: [data-model.md](./data-model.md)
