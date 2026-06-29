# runbook — reporting-service

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
- Monitorear tiempo de generación de reportes y alertar si supera el umbral configurado.

## Fallos comunes

| Síntoma | Posible causa | Acción |
|---------|---------------|--------|
| Reporte en estado pendiente indefinido | Worker de generación detenido | Reiniciar el worker y verificar la cola de trabajos. |
| Indicadores desactualizados | Eventos de dominio no procesados | Revisar consumidores de eventos y reintentos. |
| PDF no disponible | Error en motor de renderizado | Revisar logs del generador PDF y reintentar la exportación. |
