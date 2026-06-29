# runbook — auth-service

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
| 401 en todos los servicios | Token expirado o secreto JWT rotado | Verificar configuración del secreto JWT y reemitir tokens. |
| Login lento | Base de datos sobrecargada | Revisar índices en la tabla Usuario y conexiones activas. |
| Eventos no publicados | Bus de eventos caído | Revisar el broker de mensajería y reintentos. |
