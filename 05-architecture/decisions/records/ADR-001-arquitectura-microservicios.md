# ADR-0001: Arquitectura basada en microservicios

**Estado:** ACCEPTED
**Fecha:** 2026-06-22
**Autores:** Danna Barrios
**Equipos involucrados:** Arquitectura

---

## Contexto

El sistema debe controlar horarios y trazabilidad de la ejecución formativa del SENA, abarcando dominios heterogéneos: estructura institucional, actores, programas y diseño curricular, horarios, ejecución real, proyectos formativos, evidencias, reportes y auditoría. Estos dominios tienen ciclos de vida, reglas y ritmos de cambio distintos. Una arquitectura monolítica acoplaría estos dominios, dificultaría la trazabilidad por servicio, complicaría el cumplimiento de la separación de datos y limitaría la evolución independiente de cada parte.

## Decisión

Se decide construir el sistema bajo una arquitectura de microservicios con fronteras estrictas. Cada microservicio es dueño de su propio dominio y de su propia base de datos, y se comunica con los demás únicamente a través de API o eventos, sin acceder a tablas internas de otros servicios. Se separa el dominio académico-operativo SENA de la plataforma base.

## Consecuencias

### Positivas

- Cada dominio evoluciona y se despliega de forma independiente.
- Trazabilidad y auditoría claras por servicio.
- Separación estricta de datos por microservicio, alineada con los requisitos de seguridad.
- Fronteras explícitas que evitan mezclar horarios, evidencias, proyectos y diseño curricular.

### Negativas / Trade-offs

- Mayor complejidad operativa (más servicios que desplegar y monitorear).
- Necesidad de contratos y eventos bien definidos entre servicios.
- Latencia y consistencia eventual en la comunicación entre servicios.

### Riesgos

- Definir fronteras incorrectas puede generar acoplamiento o duplicación.
- Sin observabilidad adecuada, depurar flujos distribuidos es difícil.

## Alternativas consideradas

| Alternativa | Por qué se descartó |
|-------------|---------------------|
| Arquitectura monolítica | Acopla dominios con ciclos de vida distintos y dificulta trazabilidad y separación de datos. |
| Monolito modular | Mejora la organización interna, pero no garantiza fronteras de datos ni despliegue independiente. |

## Referencias

- Documento relacionado en este repo: `../../../09-microservices/service-catalog.md`
- Documento relacionado en este repo: `../../../01-context/scope.md`