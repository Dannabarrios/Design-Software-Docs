# Overview

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

## Contexto institucional

El SENA (Servicio Nacional de Aprendizaje) es la institución pública colombiana encargada de la formación profesional integral, regida por la Ley 119 de 1994. Su operación formativa se organiza en regionales, centros de formación, sedes y ambientes, y se estructura en programas de formación, diseños curriculares, competencias y Resultados de Aprendizaje (RAP).

Actualmente, el control de horarios y el seguimiento de la ejecución formativa se apoya en procesos manuales y hojas de cálculo, lo que dificulta la trazabilidad precisa de lo programado frente a lo realmente ejecutado.

## Problema

No existe una forma confiable y en tiempo real de conocer qué estaba programado, qué se ejecutó realmente, qué evidencias se entregaron y qué avance tiene cada aprendiz y cada ficha. Esto genera baja trazabilidad, dificultad para detectar desviaciones y dependencia de fuentes dispersas y no auditables.

## Objetivos

- Controlar los horarios programados y la ejecución real de las sesiones de formación.
- Registrar trazabilidad precisa de la ejecución formativa (asistencia, novedades e incidencias).
- Gestionar el avance de fichas y aprendices en tiempo de ejecución.
- Relacionar proyectos formativos con programas, diseño curricular, competencias, RAP y evidencias.
- Generar reportes, actas y documentos PDF exportables y auditables.
- Integrarse con fuentes maestras autorizadas sin reemplazar SOFIA Plus.

## Alcance

El sistema se construye bajo una arquitectura de microservicios con fronteras estrictas, separando el dominio académico-operativo SENA de la plataforma base. No reemplaza a SOFIA Plus ni crea una fuente maestra institucional sin autorización.

## Referencias

- Ley 119 de 1994 — naturaleza, misión y funciones del SENA.
- Estatuto de la Formación Profesional Integral del SENA.
- Manual de Diseño Curricular SENA.
- ADR-0002 — No reemplazo de SOFIA Plus.