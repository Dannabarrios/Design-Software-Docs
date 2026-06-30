# ADR-0001: Arquitectura basada en microservicios

**Estado:** ACCEPTED
**Fecha:** 2026-06-22
**Autores:** Danna Barrios
**Equipos involucrados:** Arquitectura

---

## Contexto

El sistema debe controlar horarios y trazabilidad de la ejecución formativa del SENA, abarcando dominios heterogéneos: estructura institucional, actores, programas y diseño curricular, horarios, ejecución real, proyectos formativos, evidencias, reportes y auditoría. Estos dominios tienen ciclos de vida, reglas y ritmos de cambio distintos. Una arquitectura monolítica acoplaría estos dominios, dificultaría la trazabilidad por servicio y limitaría la evolución independiente de cada parte.

## Decisión

Se decide construir el sistema bajo una arquitectura de microservicios con fronteras estrictas por dominio. Cada microservicio es dueño de su propio dominio y se comunica con los demás únicamente a través de API o eventos, sin acceder a las colecciones internas de otros servicios.

El sistema utiliza **una única base de datos MongoDB** con colecciones separadas por dominio. No se crean bases de datos independientes por servicio; la separación es lógica (por colección y prefijo de dominio), no física.

## Consecuencias

### Positivas

- Cada dominio evoluciona con fronteras claras y responsabilidad explícita.
- Trazabilidad y auditoría claras por servicio.
- Separación lógica de colecciones por dominio, alineada con los requisitos de organización.
- Fronteras explícitas que evitan mezclar horarios, evidencias, proyectos y diseño curricular.
- Operación simplificada al gestionar una sola instancia de base de datos.

### Negativas / Trade-offs

- Mayor complejidad en el diseño de contratos y eventos entre servicios.
- Latencia y consistencia eventual en la comunicación entre servicios.
- La separación lógica de colecciones requiere disciplina: ningún servicio consulta colecciones de otro dominio directamente.

### Riesgos

- Definir fronteras incorrectas puede generar acoplamiento o duplicación.
- Sin observabilidad adecuada, depurar flujos distribuidos es difícil.

## Alternativas consideradas

| Alternativa | Por qué se descartó |
|-------------|---------------------|
| Arquitectura monolítica | Acopla dominios con ciclos de vida distintos y dificulta trazabilidad y separación de datos. |
| Monolito modular | Mejora la organización interna, pero no garantiza fronteras de dominio ni despliegue independiente. |
| Una base de datos por servicio | Mayor complejidad operativa sin beneficio justificado para el alcance del proyecto. |

## Referencias

- Documento relacionado en este repo: `../../../09-microservices/service-catalog.md`
- Documento relacionado en este repo: `../../../01-context/scope.md`
- Documento relacionado en este repo: `../../../06-data/models.md`
