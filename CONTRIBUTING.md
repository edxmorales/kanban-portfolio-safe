# Cómo contribuir a KPS

Este framework se publica abierto a propósito: la idea es que se ponga a prueba en más de un equipo y mejore con esa evidencia, no que quede congelado en su primera versión.

## Antes de proponer un cambio

Prueba el framework en tu equipo durante al menos un ciclo completo (un trimestre, idealmente) antes de proponer cambios de fondo. Los ajustes de redacción o aclaraciones no necesitan esta espera.

## Cómo proponer un cambio

1. Abre un issue describiendo: qué parte del framework no funcionó como se esperaba, en qué contexto (tamaño de equipo, tipo de trabajo, herramientas), y qué cambio propones.
2. Si ya tienes el cambio redactado, ábrelo como pull request contra `FRAMEWORK.md`, referenciando el issue.
3. Todo pull request debe explicar el problema real que resuelve — no se aceptan cambios que solo reorganizan sin cambiar el contenido, salvo que mejoren la claridad de forma evidente.
4. Los mantenedores revisan y discuten en el propio issue/PR antes de fusionar. Cambios que alteren un pilar fundamental (sección 3 de `FRAMEWORK.md`) requieren evidencia de al menos un ciclo de uso real, no solo una propuesta teórica.

## Versionado

KPS usa versionado semántico (`MAJOR.MINOR.PATCH`):

- **MAJOR**: cambia o elimina un pilar fundamental.
- **MINOR**: agrega una mecánica, rol o sección nueva sin romper lo anterior.
- **PATCH**: corrige o aclara texto existente, sin cambiar el contenido de fondo.

Cada versión publicada se registra en [`CHANGELOG.md`](./CHANGELOG.md) con la fecha, el tipo de cambio, y quién lo propuso.

## Código de conducta

Discute las ideas, no a las personas. Si compartes un ejemplo real de tu organización para ilustrar un cambio, anonimízalo — sin nombres de personas ni de empresas, salvo que quien lo comparta autorice explícitamente lo contrario.
