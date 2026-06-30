# Topología de despliegue

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

## Principio

Cada microservicio se despliega como una unidad independiente en un contenedor propio. Todos los servicios comparten una única instancia de base de datos MongoDB, sobre la que cada servicio opera exclusivamente en sus propias colecciones (RNF-003, ADR-0001).

## Despliegue local (Docker)

Para desarrollo local, cada servicio se ejecuta en un contenedor Docker. El entorno se levanta de forma reproducible mediante un archivo de composición de contenedores que incluye todos los servicios y la instancia MongoDB compartida (RNF-010).

- Cada servicio tiene su propia imagen de contenedor.
- La base de datos MongoDB corre en un contenedor dedicado accesible por todos los servicios.
- Las variables de entorno (conexión a BD, puertos, claves) se gestionan por archivo de configuración de entorno, nunca en el código fuente.
- El entorno local replica la separación lógica de colecciones del entorno de producción.

## Despliegue futuro (Kubernetes)

La arquitectura está diseñada para ejecutarse en Kubernetes en ambientes superiores (RNF-010). Cada microservicio se empaqueta como un Pod independiente con su propio Deployment. La instancia MongoDB puede correr como StatefulSet o como servicio administrado externo según la infraestructura disponible.

## Ambientes

Los ambientes están alineados con la estrategia de ramas del repositorio (ver [`00-governance/git-conventions.md`](../00-governance/git-conventions.md)):

| Ambiente | Rama asociada | Propósito | Quién despliega |
|----------|--------------|-----------|-----------------|
| **dev** | `dev` / `hu-*-dev` | Integración continua del trabajo en desarrollo. Recibe PRs de ramas `hu-*-dev`. | Equipo de desarrollo |
| **qa** | `qa` / `hu-*-qa` | Validación funcional y técnica de los cambios integrados. | Equipo de QA |
| **staging** | `release/*` | Versión candidata a producción. Acumula HUs de una iteración antes del release. | Equipo de arquitectura |
| **main** | `main` | Documentación y artefactos estables. Solo recibe PRs desde `release/*`. | Aprobación del equipo |

## Flujo de promoción entre ambientes

```
hu-*-dev  ──PR──►  dev  ──PR──►  qa  ──PR──►  release/*  ──PR──►  main
```

Un artefacto solo avanza al siguiente ambiente si el anterior lo aprobó. Los hotfixes críticos en `main` siguen el flujo `fix/doc-*` → `main` → cherry-pick a `qa` y `dev`.
