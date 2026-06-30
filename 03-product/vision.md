# Visión del producto

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

## Para quién es

La plataforma está dirigida a los actores del proceso formativo del SENA que necesitan visibilidad y control sobre la programación y ejecución de la formación:

- **Coordinadores académicos** — planifican horarios, gestionan fichas, hacen seguimiento al avance de aprendices y detectan desviaciones.
- **Instructores** — registran la ejecución real de sus sesiones, la asistencia y las novedades.
- **Actores autorizados** — coordinadores de área, directivos y personal de seguimiento que consultan reportes, actas y tableros de avance.

## Problema que resuelve

Actualmente no existe una forma confiable y en tiempo real de conocer qué estaba programado, qué se ejecutó realmente, qué evidencias se entregaron y qué avance tiene cada aprendiz y cada ficha. El control de horarios y la trazabilidad de la ejecución formativa dependen de procesos manuales y hojas de cálculo dispersas, lo que impide detectar desviaciones a tiempo, dificulta la auditoría y genera dependencia de fuentes no auditables.

## Propuesta de valor

La plataforma centraliza en un único sistema:

- La programación de horarios por ficha, instructor, ambiente y periodo.
- El registro de la ejecución real de cada sesión frente a lo programado.
- La trazabilidad de asistencia, novedades e incidencias.
- El avance de cada aprendiz por RAP, evidencia y proyecto formativo.
- Las dependencias y el estado de los proyectos formativos.
- Los reportes, actas y documentos PDF exportables y auditables.
- Las alertas y desviaciones en tiempo real.

Todo esto sin reemplazar SOFIA Plus ni duplicar su rol como fuente maestra institucional.

## Objetivos del producto

- Controlar la diferencia entre lo programado y lo ejecutado en tiempo real.
- Registrar trazabilidad precisa y auditable de la ejecución formativa.
- Medir el avance de aprendices y fichas por RAP, evidencia y proyecto.
- Relacionar proyectos formativos con competencias, RAP y diseño curricular.
- Generar reportes, actas y PDF exportables para soporte a la gestión.
- Integrarse con fuentes maestras autorizadas sin reemplazarlas.
- Exponer contratos y eventos por microservicio para trazabilidad distribuida.

## Principios del producto

- **Modular** — cada capacidad es responsabilidad de un único microservicio con frontera estricta y base de datos propia.
- **Auditable** — toda acción relevante queda registrada; los reportes y PDF son soportes inmutables y trazables.
- **Trazable** — la correlación entre lo programado, lo ejecutado, las evidencias y el avance es siempre visible y verificable.
- **No reemplaza SOFIA Plus** — la plataforma integra con fuentes maestras existentes; no crea una fuente maestra institucional paralela ni autorizada.
- **Extensible** — la arquitectura de microservicios permite incorporar nuevas capacidades sin afectar las existentes.
