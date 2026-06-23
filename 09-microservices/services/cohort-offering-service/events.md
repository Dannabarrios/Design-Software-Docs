# events — cohort-offering-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `FichaCreated` | Se crea una ficha. |
| `OfferingPublished` | Se publica una oferta formativa. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| `ProgramUpdated` | program-catalog-service | Actualiza la referencia del programa asociado a la oferta. |
