# events — program-catalog-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `ProgramCreated` | Se crea un programa de formación. |
| `ProgramUpdated` | Se actualiza un programa de formación. |
| `CurriculumDesignUpdated` | Se modifica el diseño curricular de un programa. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| — | — | El servicio no consume eventos en esta versión. |