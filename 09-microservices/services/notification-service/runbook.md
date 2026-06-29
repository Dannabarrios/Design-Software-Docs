# runbook — notification-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Guía operativa del servicio.

## Despliegue

Servicio independiente con base de datos propia. Despliegue reproducible local y futuro por Kubernetes (ver 10-devops). Requiere configuración de credenciales para cada canal de envío activo.

## Healthcheck

- Endpoint de salud: `GET /health`.

## Observabilidad

- Logs estructurados con `correlation_id`.
- Métricas y trazas expuestas según los lineamientos de observability-service.
- Monitorear la tasa de `NotificationFailed` para detectar problemas en canales externos.

## Fallos comunes

| Síntoma | Posible causa | Acción |
|---------|---------------|--------|
| Notificaciones no llegan | Canal externo caído o credenciales vencidas | Verificar estado del canal y renovar credenciales. |
| Cola de notificaciones creciente | Consumidor de eventos lento o detenido | Revisar workers del consumidor y escalar si es necesario. |
| Eventos no procesados | Bus de eventos caído | Revisar el broker de mensajería y reintentos. |
