# Lineamientos de revisión

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Lineamientos para la revisión de cambios en el repositorio. Todo cambio entra por Pull Request; ningún cambio se aplica directamente sobre ramas protegidas (ver [`00-governance/git-conventions.md`](../00-governance/git-conventions.md)).

## Regla base

Las ramas `dev`, `qa`, `staging` (`release/*`) y `main` son protegidas. Todo cambio —documental o de implementación— debe llegar a estas ramas únicamente a través de un Pull Request revisado y aprobado. No se permiten push directos a ramas protegidas.

## Checklist de revisión de PR

Antes de aprobar un Pull Request, el revisor verifica que se cumplen todos los puntos siguientes:

### Definition of Done

- [ ] El cambio fue aprobado por al menos un revisor.
- [ ] El archivo está enlazado desde el `README.md` de su sección.
- [ ] El estado del archivo cambió a 🟢 si corresponde.
- [ ] Los enlaces relativos dentro del documento funcionan correctamente.
- [ ] El documento no contiene información sensible (credenciales, tokens, datos personales).
- [ ] El CHANGELOG fue actualizado si el cambio modifica gobernanza, estructura de carpetas o un contrato compartido (API, modelo de datos, convenciones de Git).

### Definition of Ready (para entrar en revisión)

- [ ] El documento tiene título, estado, fecha y autor o equipo responsable.
- [ ] Tiene al menos las secciones de Contexto y Contenido con texto real (no vacías ni solo con comentarios).
- [ ] Está enlazado desde el `README.md` de su sección.
- [ ] Los diagramas referenciados existen en `08-uml/` con fuente editable.
- [ ] Fue revisado por el autor antes del PR.

### Convenciones del repositorio

- [ ] El mensaje de commit sigue el formato Conventional Commits: `<type>(NN-section): short description in English`.
- [ ] El tipo de commit es uno de los permitidos: `docs`, `fix`, `chore`, `refactor`.
- [ ] La rama sigue el formato correcto según su propósito (`hu-<numero>-dev`, `feat/doc-*`, `fix/doc-*`, etc.).

### Fronteras de servicios (para cambios de arquitectura o implementación)

- [ ] El cambio no cruza fronteras de microservicio: ningún servicio accede a colecciones de otro.
- [ ] Si se modifica un contrato de API o evento, se actualiza también la prueba contractual correspondiente.
- [ ] Si se modifica `07-api/contracts/openapi/`, el cambio fue revisado por arquitectura.

## Rol de CODEOWNERS

Las secciones críticas del repositorio tienen propietarios asignados que deben aprobar cualquier cambio sobre esas rutas. El archivo `CODEOWNERS` define estas asignaciones. Un PR que toca una ruta con CODEOWNER requiere la aprobación explícita de ese propietario además de la revisión general.

Secciones que requieren aprobación de CODEOWNER:

| Ruta | Justificación |
|------|--------------|
| `05-architecture/decisions/` | Los ADR son decisiones técnicas de alto impacto. |
| `07-api/contracts/openapi/` | Los contratos publicados afectan a todos los consumidores. |
| `00-governance/` | Las reglas de gobernanza afectan a todo el repositorio. |
| `04-requirements/` | Los cambios de requisitos tienen impacto transversal. |

## Criterios de aprobación y rechazo

### Se aprueba cuando

- Todos los puntos del checklist están marcados.
- El contenido es consistente con el resto de la documentación del repositorio.
- No introduce información no confirmada, inventada o fuera del alcance del proyecto.
- Los comentarios del revisor fueron resueltos o respondidos.

### Se rechaza (solicitar cambios) cuando

- Falta al menos un punto obligatorio del checklist.
- El mensaje de commit no sigue Conventional Commits.
- El documento introduce supuestos no validados o contradice un ADR o RNF existente.
- El archivo no está enlazado desde el `README.md` de su sección.
- Se detecta información sensible en el contenido.

### Se bloquea (no merge) cuando

- El PR toca una ruta con CODEOWNER y ese propietario no aprobó.
- El PR apunta a una rama protegida sin haber pasado por la rama intermedia correspondiente en el flujo `dev → qa → release/* → main`.
