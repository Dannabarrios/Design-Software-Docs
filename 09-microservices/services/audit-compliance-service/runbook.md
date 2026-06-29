# runbook — audit-compliance-service

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura

Guía operativa del servicio.

## Despliegue

Servicio independiente con base de datos propia. Despliegue reproducible local y futuro por Kubernetes (ver 10-devops). La base de datos debe configurarse con protección contra DROP y DELETE masivos.

## Healthcheck

- Endpoint de salud: `GET /health`.

## Observabilidad

- Logs estructurados con `correlation_id`.
- Métricas y trazas expuestas según los lineamientos de observability-service.
- Alertar si el volumen de inserciones cae a cero durante más de 5 minutos (indica posible corte del bus de eventos).

## Fallos comunes

| Síntoma | Posible causa | Acción |
|---------|---------------|--------|
| Registros no llegan | Bus de eventos caído | Revisar el broker de mensajería y reintentos pendientes. |
| Consultas lentas en /audit-logs | Tabla sin índice por fecha o usuario | Revisar plan de consulta y agregar índice si corresponde. |
| Disco lleno | Política de retención no ejecutada | Verificar ejecución del job de retención y liberar espacio. |
