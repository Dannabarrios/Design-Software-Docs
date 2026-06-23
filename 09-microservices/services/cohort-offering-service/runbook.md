# runbook — cohort-offering-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Guía operativa del servicio.

## Despliegue

Servicio independiente con base de datos propia. Despliegue reproducible local y futuro por Kubernetes (ver 10-devops).

## Healthcheck

- Endpoint de salud: `GET /health`.

## Observabilidad

- Logs estructurados con `correlation_id`.
- Métricas y trazas expuestas según los lineamientos de observability-service.

## Fallos comunes

| Síntoma | Posible causa | Acción |
|---------|---------------|--------|
| 5xx en endpoints | Base de datos no disponible | Verificar conexión y estado de la BD del servicio. |
| Eventos no publicados | Bus de eventos caído | Revisar el broker de mensajería y reintentos. |
