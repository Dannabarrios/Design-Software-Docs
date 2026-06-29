# runbook — integration-sync-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Guía operativa del servicio.

## Despliegue

Servicio independiente con base de datos propia. Despliegue reproducible local y futuro por Kubernetes (ver 10-devops). Requiere acceso de red hacia las fuentes maestras externas.

## Healthcheck

- Endpoint de salud: `GET /health`.

## Observabilidad

- Logs estructurados con `correlation_id`.
- Métricas y trazas expuestas según los lineamientos de observability-service.
- Alertar si un trabajo programado no inicia en la ventana esperada.

## Fallos comunes

| Síntoma | Posible causa | Acción |
|---------|---------------|--------|
| SyncJobFailed repetido | Fuente externa no disponible | Verificar conectividad de red y credenciales de la fuente maestra. |
| Datos desactualizados en servicios internos | Trabajo de sincronización no ejecutado | Revisar el scheduler y lanzar un trabajo manual desde /sync-jobs. |
| Eventos no publicados | Bus de eventos caído | Revisar el broker de mensajería y reintentos. |
