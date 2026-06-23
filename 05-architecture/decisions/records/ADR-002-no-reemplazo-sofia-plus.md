# ADR-0002: No reemplazo de SOFIA Plus

**Estado:** ACCEPTED
**Fecha:** 2026-06-22
**Autores:** Danna Barrios
**Equipos involucrados:** Arquitectura

---

## Contexto

SOFIA Plus es el sistema de información institucional del SENA para la gestión de la oferta educativa y actúa como fuente maestra de datos institucionales (fichas, aprendices, instructores, programas). El sistema de trazabilidad podría confundirse con un reemplazo de esa plataforma, lo que aumentaría el riesgo normativo y haría perder el foco del producto.

## Decisión

Se decide que el sistema no será una nueva plataforma SOFIA Plus. Su alcance se limita a la trazabilidad de ejecución, horarios, proyectos formativos, avance en tiempo de ejecución, evidencias, alertas, reportes e integración con fuentes maestras autorizadas. La relación con SOFIA Plus y otras fuentes maestras será de integración y sincronización, nunca de reemplazo.

## Consecuencias

### Positivas

- Mantiene el foco del producto en trazabilidad y ejecución.
- Reduce el riesgo normativo e institucional.
- Respeta las fuentes maestras autorizadas existentes.

### Negativas / Trade-offs

- Dependencia de la disponibilidad e integración con fuentes externas.
- Algunos datos maestros no son propiedad del sistema y deben sincronizarse.

### Riesgos

- Intentar convertir el sistema en fuente maestra sin autorización desviaría el alcance y aumentaría el riesgo normativo.

## Alternativas consideradas

| Alternativa | Por qué se descartó |
|-------------|---------------------|
| Construir una plataforma institucional completa | Fuera de alcance, alto riesgo normativo y duplicaría a SOFIA Plus. |
| Replicar y volverse fuente maestra | Genera conflicto de propiedad del dato y riesgo legal. |

## Referencias

- Documento relacionado en este repo: `../../../01-context/scope.md`
- Documento relacionado en este repo: `../../../15-project-control/open-questions.md`