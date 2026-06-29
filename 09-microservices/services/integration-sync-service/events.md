# events — integration-sync-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Eventos de dominio publicados por el servicio. Todos incluyen `event_id`, `event_type`, `occurred_at`, `source`, `correlation_id` y `data`.

## Eventos publicados

| Evento | Cuándo se emite |
|--------|-----------------|
| `SyncJobStarted` | Inicia un trabajo de sincronización. |
| `SyncJobCompleted` | Un trabajo de sincronización finaliza sin errores. |
| `SyncJobFailed` | Un trabajo de sincronización termina con errores. |
| `ExternalDataSynced` | Un registro de fuente externa fue procesado y publicado al dominio correspondiente. |

## Eventos consumidos

| Evento | Origen | Uso |
|--------|--------|-----|
| — | — | El servicio no consume eventos internos; se activa por schedule programado o solicitud manual. |
