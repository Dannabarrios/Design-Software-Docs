# Incorporación técnica

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Guía de entrada al proyecto para nuevos integrantes técnicos. Explica cómo está organizado el repositorio, las reglas de gobierno, la estrategia de trabajo y dónde encontrar cada tipo de información.

## Qué es este repositorio

Este es el repositorio de **documentación de diseño de software** del sistema de horarios y trazabilidad formativa del SENA. No contiene código de implementación; contiene toda la documentación de arquitectura, dominio, requisitos, microservicios, decisiones técnicas y gobierno del proyecto.

## Estructura del repositorio

El repositorio está organizado en 16 secciones numeradas. Cada sección tiene su propio `README.md` como índice:

| Sección | Contenido |
|---------|-----------|
| [`00-governance/`](../00-governance/) | Reglas del repositorio: git conventions, definition of ready, definition of done. |
| [`01-context/`](../01-context/) | Contexto institucional, problema, objetivos y alcance del sistema. |
| [`02-domain/`](../02-domain/) | Mapa de dominio, entidades, reglas de negocio y eventos de dominio. |
| [`03-product/`](../03-product/) | Visión del producto, roadmap y backlog de alto nivel. |
| [`04-requirements/`](../04-requirements/) | Requisitos funcionales, no funcionales, historias de usuario y matriz de trazabilidad. |
| [`05-architecture/`](../05-architecture/) | Vista de arquitectura, despliegue, aspectos transversales y ADR. |
| [`06-data/`](../06-data/) | Modelo de datos, diccionario de entidades y estrategia de migración. |
| [`07-api/`](../07-api/) | Lineamientos de API REST, autenticación y contratos OpenAPI. |
| [`08-uml/`](../08-uml/) | Diagramas UML del sistema. |
| [`09-microservices/`](../09-microservices/) | Catálogo de servicios, patrones de comunicación y documentación por servicio. |
| [`10-devops/`](../10-devops/) | Entorno local, CI/CD y ambientes. |
| [`11-quality/`](../11-quality/) | Estrategia de pruebas y lineamientos de revisión de código. |
| [`12-ux-ui/`](../12-ux-ui/) | Diseño de experiencia e interfaz de usuario. |
| [`13-operations/`](../13-operations/) | Observabilidad, gestión de incidentes y respaldo. |
| [`14-training/`](../14-training/) | Manuales de usuario, administrador y onboarding técnico. |
| [`15-project-control/`](../15-project-control/) | Control del proyecto: preguntas abiertas, riesgos y seguimiento. |

## Por dónde empezar

El orden recomendado de lectura para un nuevo integrante:

1. **[`01-context/overview.md`](../01-context/overview.md)** — Qué es el sistema, qué problema resuelve y cuál es su alcance.
2. **[`05-architecture/overview.md`](../05-architecture/overview.md)** — Estilo arquitectónico, agrupación de servicios y comunicación.
3. **[`05-architecture/decisions/`](../05-architecture/decisions/)** — ADR-001 (microservicios) y ADR-002 (no reemplaza SOFIA Plus): las dos decisiones fundacionales.
4. **[`09-microservices/service-catalog.md`](../09-microservices/service-catalog.md)** — Los 16 servicios con su módulo y responsabilidad.
5. **[`00-governance/git-conventions.md`](../00-governance/git-conventions.md)** — Estrategia de ramas y reglas de commits antes de hacer cualquier cambio.

## Reglas de gobierno

Todo el gobierno del repositorio está en [`00-governance/`](../00-governance/). Los tres documentos clave:

| Documento | Para qué sirve |
|-----------|----------------|
| [`git-conventions.md`](../00-governance/git-conventions.md) | Estrategia de ramas, formato de commits y flujo de PRs. |
| [`definition-of-ready.md`](../00-governance/definition-of-ready.md) | Criterios que un documento debe cumplir antes de entrar en revisión. |
| [`definition-of-done.md`](../00-governance/definition-of-done.md) | Criterios que un documento debe cumplir para considerarse completo. |

## Estrategia de ramas y PRs

El repositorio usa ramas protegidas y Pull Requests para todo cambio:

```
hu-*-dev  ──PR──►  dev  ──PR──►  qa  ──PR──►  release/*  ──PR──►  main
```

- Todo trabajo nuevo parte de una rama `hu-<numero>-dev` creada desde `dev`.
- No se hace push directo a `dev`, `qa` ni `main`.
- Los mensajes de commit siguen Conventional Commits: `<type>(NN-section): short description in English`.
- Tipos permitidos: `docs`, `fix`, `chore`, `refactor`.

Ver el flujo completo en [`00-governance/git-conventions.md`](../00-governance/git-conventions.md).

## Microservicios

Cada uno de los 16 servicios tiene su propia carpeta en `09-microservices/services/<servicio>/` con:

| Archivo | Contenido |
|---------|-----------|
| `overview.md` | Responsabilidad, módulo y prioridad del servicio. |
| `api-contract.md` | Endpoints principales y reglas del contrato de API. |
| `data-model.md` | Entidades y relaciones propias del servicio. |
| `events.md` | Eventos de dominio que publica y consume. |
| `runbook.md` | Guía operativa: healthcheck, observabilidad y fallos comunes. |

## Arquitectura y decisiones

- La arquitectura general está en [`05-architecture/`](../05-architecture/).
- Las decisiones técnicas relevantes están en [`05-architecture/decisions/records/`](../05-architecture/decisions/records/) como ADR (Architecture Decision Records).
- Toda nueva decisión técnica de alto impacto debe registrarse como un ADR siguiendo la plantilla en `05-architecture/decisions/_template-adr.md`.

## Preguntas abiertas

Antes de implementar cualquier funcionalidad, revisar [`15-project-control/open-questions.md`](../15-project-control/open-questions.md). Contiene preguntas sin respuesta que afectan decisiones de diseño e implementación. No suponer respuestas no confirmadas.
