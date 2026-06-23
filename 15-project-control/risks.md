# Riesgos

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Arquitectura / Gestión

Registro de riesgos del proyecto con su impacto, probabilidad y mitigación.

| ID | Riesgo | Impacto | Probabilidad | Mitigación |
|------|--------|---------|--------------|------------|
| R-01 | Confundir el alcance con un reemplazo de SOFIA Plus | Alto | Media | Mantener las fuentes maestras como integración/sincronización, no como reemplazo (ADR-002). |
| R-02 | Definir fronteras incorrectas entre microservicios | Alto | Media | Documentar fronteras, contratos y eventos por servicio antes de implementar. |
| R-03 | Inventar reglas internas SENA no confirmadas | Alto | Media | Toda regla institucional debe trazarse a fuente o decisión del product owner (regla de oro). |
| R-04 | Manejo inadecuado de datos personales de aprendices | Alto | Baja | Aplicar mínimo privilegio y protección de datos (Ley 1581 de 2012). |
| R-05 | Complejidad operativa por número de servicios | Medio | Media | Observabilidad desde el inicio: logs, métricas y trazas distribuidas. |
| R-06 | Dependencia de fuentes externas no disponibles | Medio | Media | Definir mecanismos de sincronización y manejo de fallos de integración. |
| R-07 | Pérdida de trazabilidad entre lo programado y lo ejecutado | Alto | Baja | Correlation ID obligatorio en APIs y eventos. |