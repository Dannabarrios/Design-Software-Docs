# Autenticación y autorización

> Estado: 🟢 | Última actualización: 2026-06-22
> Autor: Danna Barrios | Equipo: Documentación

Estrategia de autenticación y autorización del sistema. La gestión de identidad, tokens y permisos es responsabilidad exclusiva de `auth-service` (RNF-001).

## Responsabilidades de auth-service

`auth-service` es el único servicio del sistema que emite y valida tokens de acceso. Sus responsabilidades son:

- Gestionar usuarios, roles y permisos.
- Emitir tokens de acceso tras una autenticación exitosa.
- Validar tokens en solicitudes entrantes.
- Proporcionar la identidad del actor autenticado a los demás servicios.

Ningún otro servicio gestiona credenciales ni emite tokens.

## Flujo de autenticación y autorización

1. El actor (usuario del sistema) se autentica ante `auth-service` con sus credenciales.
2. `auth-service` valida las credenciales y emite un token de acceso.
3. El actor incluye el token en el encabezado `Authorization: Bearer <token>` en cada solicitud al sistema.
4. El servicio receptor valida el token (directamente o delegando a `auth-service`).
5. Si el token es válido, el servicio extrae la identidad del actor y verifica que tenga el permiso necesario para la operación solicitada.
6. El `correlation_id` se propaga junto con la identidad del actor en todas las llamadas internas (RNF-004).

## Modelo de autorización

La autorización sigue el principio de **mínimo privilegio** (RNF-001): cada actor tiene acceso únicamente a los recursos y operaciones que su rol permite.

- **Roles:** agrupaciones de permisos asignadas a usuarios según su función institucional (coordinador, instructor, actor autorizado, etc.).
- **Permisos:** acciones específicas sobre recursos concretos del sistema.
- Un usuario puede tener uno o más roles; los permisos se acumulan.
- Ningún actor accede a recursos fuera del alcance de sus roles asignados.

## Propagación de identidad entre servicios

Cuando un servicio necesita llamar a otro como parte de una operación:

- Propaga el token de acceso original o la identidad del actor en los encabezados de la llamada interna.
- Propaga el `correlation_id` en el encabezado `X-Correlation-ID`.
- El servicio receptor aplica las mismas reglas de validación y autorización.

## Preguntas abiertas

La siguiente pregunta de [`15-project-control/open-questions.md`](../15-project-control/open-questions.md) tiene impacto directo en el modelo de autorización:

| # | Pregunta | Estado |
|---|----------|--------|
| Q-03 | ¿Qué roles institucionales pueden ver información de aprendices? | ABIERTA |

Hasta que Q-03 esté resuelta, la definición detallada de roles con acceso a datos de aprendices queda pendiente y no debe implementarse con supuestos no validados.
