# Changelog

Todos los cambios notables de este framework se documentan aquí. El formato sigue versionado semántico (`MAJOR.MINOR.PATCH`), descrito en [`CONTRIBUTING.md`](./CONTRIBUTING.md).

## [1.13.0]

### Agregado

- `docs/plan-implementacion.xlsx`: la hoja "Seguimiento de proyectos" agrega la columna "Responsable de QA (para indicadores de WIP)" junto a la de desarrollo (renombrada "Responsable de desarrollo (para indicadores de WIP)"). La tabla de capacidad por persona en "Resumen" (sección 9.2) ahora suma los ítems "En curso" tanto de la columna de desarrollo como de la de QA, para que la carga de QA también quede visible en el índice de concentración y el % de cumplimiento de WIP. La matriz de prioridad se recorrió de las columnas S–V a T–W para hacerle espacio a la columna nueva; la fórmula de "Prioridad" se actualizó en consecuencia. 50 fórmulas verificadas sin errores.

## [1.12.0]

### Agregado

- `docs/plan-implementacion.xlsx`: nueva hoja "Roles y gobierno" (sección 5 del framework) — un registro de quién tiene cada rol de gobierno y quién es su respaldo nombrado. Trae los 7 roles ya listados, con una fila de "Líder de Flujo de Valor" por cada flujo de valor de ejemplo (los mismos que usa "Seguimiento de proyectos"), y columnas "Titular"/"Respaldo" en amarillo para completar con nombres reales. "Cómo usar" se actualizó para explicarla.
- `docs/plan-implementacion.xlsx`: la columna "Estado" de "Seguimiento de proyectos" suma el valor "Cancelado", con su conteo correspondiente en el panel "Resumen".

## [1.11.0]

### Agregado

- `docs/plan-implementacion.xlsx`: la hoja "Seguimiento de proyectos" suma tres columnas — "Fecha real de inicio de desarrollo", "Fecha real de cierre" y "Responsable principal (para indicadores de WIP)" — que alimentan una nueva sección de indicadores en la hoja "Resumen": Lead time y Cycle time promedio, Eficiencia de flujo, % de entrega a tiempo (Fecha fija), y una tabla de capacidad por persona con Tope de WIP editable que calcula el Índice de concentración y el % de cumplimiento de WIP (sección 9 del framework). La matriz de prioridad se recorrió de las columnas P–S a S–V para hacerle espacio a las columnas nuevas; la fórmula de "Prioridad" se actualizó en consecuencia. 49 fórmulas verificadas sin errores.

## [1.10.0]

### Agregado

- Sección 6.4 (nueva), en `FRAMEWORK.md` y `FRAMEWORK.en.md`: **Iniciativas transversales con ejecución independiente por mercado.** Resuelve un vacío que la sección 6.2 (dependencias entre flujos de valor) no cubría: una misma capacidad desplegada en varios mercados que pueden avanzar, bloquearse o completarse de forma independiente. Regla: una tarjeta por mercado, nunca una tarjeta agregada, para que un bloqueo puntual en un mercado no arrastre el estado visible de los demás ni retenga el WIP de la persona asignada. Incluye el criterio de cuándo dividir (al pasar de validación/POC a ejecución aprobada, no antes) y un indicador nuevo que extiende la sección 9.1 (% de mercados completados por iniciativa transversal). Se actualiza la Tabla de contenido / Table of contents de ambos documentos.

## [1.9.1]

### Corregido

- `FRAMEWORK.md` y `FRAMEWORK.en.md`: se agrega una tabla de contenido al inicio de cada documento, con enlaces verificados uno por uno (43 enlaces internos en cada archivo, cero rotos) contra los encabezados reales generados por el renderizador de GitHub.

## [1.9.0]

### Agregado

- `FRAMEWORK.en.md` (nuevo): traducción completa al inglés de `FRAMEWORK.md`, con enlaces cruzados entre ambas versiones desde la cabecera de cada documento y desde `README.md`.

### Corregido

- `FRAMEWORK.md`: pasada de lenguaje en todo el documento para que se lea más fácil — oraciones más cortas, menos encadenamiento de guiones largos, sin cambiar ninguna regla, número de sección ni ancla interna (los enlaces desde los casos de aplicación y `README.md` siguen funcionando igual).

## [1.8.0]

### Agregado

- `docs/plan-implementacion.xlsx` (nueva plantilla): hoja de ruta de implementación de 10 pasos, más una hoja nueva de **seguimiento de proyectos** — el registro de cada solicitud real, con una prioridad que se calcula sola combinando impacto de negocio y tamaño del esfuerzo (matriz de prioridad, sin fórmulas ocultas). Incluye una hoja "Cómo usar" y un panel "Resumen" que se actualiza solo a partir de las otras dos hojas. Cumple el pendiente de plantillas concretas declarado desde la versión 1.0.0. Sin mencionar herramientas de gestión de trabajo específicas — en lenguaje de negocio, lista para copiar y adaptar por cualquier equipo.

## [1.7.2]

### Corregido

- Tabla de la sección 0.1: el frente 3 (Aplicaciones) pasa de "fuera de alcance por completo" a "parcial, de forma indirecta" — si la organización ya tiene un inventario interno de aplicaciones, servicios, desarrollos propios y herramientas operativas, ese inventario alimenta directamente cómo se agrupan los flujos de valor de KPS (pilar 5). Se ajusta también el párrafo resumen para reflejar que solo el frente 1 (Escuchar) queda fuera de alcance por completo.

## [1.7.1]

### Corregido

- Tabla de la sección 0.1: los frentes 2 (Infraestructura), 4 (Ciberseguridad) y 9 (Madurez Digital) pasan de "fuera de alcance por completo" a "parcial, de forma indirecta" — el caso de aplicación 1 mostró que, aunque KPS no diagnostica infraestructura ni seguridad, sus hallazgos sí se integran directamente al backlog priorizado de KPS una vez producidos por otro medio; y el frente 9 se cubre parcialmente por la Sección 10 (apalancamiento con IA). Se distingue explícitamente "el diagnóstico en sí" (fuera de alcance) de "la integración de sus hallazgos" (parcial).

## [1.7.0]

### Agregado

- `docs/caso-aplicacion-01-diagnostico-seguridad.md` (nuevo): primer caso de aplicación real anonimizado del framework — cumple el pendiente declarado desde la versión 1.0.0 ("casos de estudio anonimizados de equipos que lo hayan aplicado"). Documenta el frente 4 (Ciberseguridad) del Diagnóstico 360° de TI de alcance amplio (sección 0.1) y cómo se relaciona con el Diagnóstico 360 propio de KPS.
- `docs/propuesta-piloto-01.md` (nuevo): continuación del caso 1 — clasifica hallazgos reales de ese diagnóstico en clases de servicio de KPS, propone un flujo de valor de Plataforma e Infraestructura, los roles a nombrar (incluido el Representante de Valor de Negocio), y el criterio de éxito del piloto usando la línea base que el propio diagnóstico ya capturó.
- Enlaces cruzados desde `README.md` hacia ambos documentos nuevos, en una sección "Casos de aplicación real".

## [1.6.0]

### Agregado

- Sección 0.1 (nueva): relación entre el Diagnóstico 360 de KPS y una metodología más amplia de diagnóstico 360° para transformación de TI (los diez frentes que recorrería un Director de TI al llegar a una organización: Escuchar, Infraestructura, Aplicaciones, Ciberseguridad, Proyectos y Contratos, Procesos de TI, Presupuesto, Talento Humano, Madurez Digital, Presentar y Priorizar). Incluye tabla de mapeo explícito de qué frentes cubre el Diagnóstico 360 de KPS (parcial o totalmente) y cuáles quedan fuera de alcance a propósito, para dejar claro que KPS diagnostica la capa de flujo de trabajo, no la función de TI completa.

## [1.5.0]

### Agregado

- Rol nuevo en la sección 5: **Representante de Valor de Negocio**, única fuente aceptada del componente de valor de negocio (costo de demora) del WSJF — cierra el vacío de quién le da ese número al framework.
- Columna "Respaldo" en la tabla de roles y gobierno: cada rol de autoridad (Responsable de Flujo de Portafolio, Aprobador de Clase de Servicio, Facilitador del Ritual Semanal, Líder de Flujo de Valor, Representante de Valor de Negocio, Dueño de Calidad del Flujo) tiene ahora un respaldo nombrado explícitamente, para que la gobernanza del framework no tenga el mismo bus factor que busca eliminar en el equipo.
- Sección 5.1 (nueva): escalamiento y desacuerdos entre roles, en tres niveles — dentro de un flujo de valor, entre un flujo y la vista de portafolio, y lo que no se resuelve en el ritual semanal se lleva a la recalibración trimestral.
- Sección 6.2 (nueva): dependencias entre flujos de valor — cómo se declaran en el refinamiento, cómo se vuelven visibles en la vista única de capacidad, y el indicador que expone cuándo los flujos de valor están mal agrupados.
- Sección 6.3 (nueva): onboarding de una persona nueva o rotación interna entre flujos de valor — tope de WIP reducido al entrar, punto de referencia informal, acceso a documentación existente, y transferencia de conocimiento antes de rotar (extiende la lógica de cierre de contrato freelance de 6.1 al caso interno).
- Definición de Listo, en concreto: checklist explícito de entrada a "En desarrollo" en la sección 7, como contraparte de la Definición de Hecho ya existente, con autoridad del Facilitador del Ritual Semanal para devolver a refinamiento lo que no la cumpla.
- Criterio de decisión (go/no-go) para cerrar el piloto en la sección 9.9: umbral explícito de cuántos indicadores del puntaje compuesto deben mejorar para expandir, ajustar y repetir, o documentar como aprendizaje negativo.
- Hoja de ruta (sección 11): nuevo paso explícito para nombrar cada rol con su respaldo y designar el Representante de Valor de Negocio antes de instalar WSJF; el paso del piloto ahora exige acordar el criterio de éxito antes de empezar, no después de ver resultados.

## [1.4.0]

### Agregado

- Sección 12 (nueva): presupuesto y dotación — costo de mantener el negocio vs. cambiarlo, costo real de dotación interna vs. freelance (incluyendo el costo oculto de transferencia de conocimiento), categorías mínimas de presupuesto operativo, cómo el presupuesto se conecta con el piso de capacidad por iniciativa, e indicadores de eficiencia de costo. La sección "Cómo evoluciona este framework" pasa a ser la sección 13.
- Gráfico-póster de una sola pieza (`docs/kps-framework-overview.svg` / `.png`), estilo compendio imprimible: Diagnóstico 360 como paso 0, el flujo de principio a fin con badges de WIP, un panel de "check rápido" de 8 puntos para verificar cumplimiento en el ritual semanal, y una tira de roles — todo en iconos de línea, sin texto explicativo largo.
- Nota explícita en el resumen ejecutivo: el Diagnóstico 360 es el punto de entrada obligatorio del framework, antes de abordar cualquier proyecto o iniciativa.

### Corregido

- Iconos duplicados en la primera versión del gráfico-póster: "Revisión" ahora usa un ícono propio (antes compartía el de "Refinar"), y "Facilitador del Ritual Semanal" ahora usa un ícono propio (antes compartía el de "Guardia Rotativa").

## [1.3.0]

### Agregado

- Sección 0 (nueva): Diagnóstico 360 — el paso obligatorio antes de instalar cualquier regla del framework, revisando capacidad real por persona, cumplimiento de WIP, estado de cada iniciativa, estado de PRs/flujo de código, y actividad real de QA. Referenciado como Paso 0 de la hoja de ruta.

## [1.2.0]

### Agregado

- Sección 6.1: modelo de dotación — criterios y reglas para decidir cuándo usar personal freelance/por contrato (trabajo tipo proyecto, con fecha de fin) y cuándo debe quedarse con personal interno (mantenimiento del negocio, soporte, deuda técnica), incluyendo cómo se refleja la capacidad freelance en la vista única de portafolio.
- Sección 9.10: mapeo explícito de los indicadores del framework contra los desperdicios clásicos de Lean (espera, exceso de WIP, retrabajo, sobreprocesamiento, conocimiento no transferido, handoffs), para anclar el sistema de medición a eficiencia y costo, no solo a velocidad.
- Sección 10 (nueva): apalancamiento con inteligencia artificial en captura/reporte diario y semanal, sugerencia de clase de servicio, apoyo a la estimación de WSJF, generación de documentación para reducir bus factor, apoyo a QA, y alertas de eficiencia — siempre acelerando reglas ya definidas por el framework, nunca reemplazando la autoridad de decisión de los roles humanos.

## [1.1.0]

### Agregado

- Sección 9 expandida de una lista simple de métricas a un sistema de medición completo: indicadores de flujo, capacidad y carga, interrupción y costo, deuda técnica, calidad, predictibilidad, un puntaje compuesto de eficiencia, la cadencia de medición (diaria/semanal/mensual/trimestral), y la tabla de indicadores para validar el piloto (antes/después/control).

## [1.0.0] — Versión inicial

Primera versión publicada del framework.

### Contenido incluido

- El problema que resuelve y los fundamentos (por qué Kanban + capa de portafolio de SAFe, y no Scrum ni SAFe completo).
- Los 7 pilares del framework: vista única de capacidad, límite de WIP por persona, clases de servicio con WSJF, piso de capacidad por iniciativa, flujos de valor, ritual semanal, recalibración trimestral.
- 5 mecánicas propias: costo de interrupción, guardia rotativa, interés de deuda técnica, autoridad de clase de servicio, visibilidad radical.
- Roles y gobierno con tabla de responsabilidad/autoridad.
- Modelo de gestión de equipos por flujo de valor y pool habilitante compartido.
- Integración de QA al flujo (shift-left, WIP propio de QA, Definición de Listo/Hecho).
- Flujo de infraestructura de principio a fin: ramas, PRs, pipeline de CI, ambientes, feature flags, rollback, ventana de observación post-despliegue.
- Métricas de seguimiento.
- Hoja de ruta de implementación en 7 pasos.
- Anexos: SAFe en profundidad (competencias, configuraciones, principios, comparación con Nexus/LeSS/Scrum@Scale) y glosario de términos.

### Pendiente para próximas versiones

- Casos de estudio anonimizados de equipos que lo hayan aplicado.
- Plantillas concretas (tablero, definición de listo/hecho, formato de la tarea de flujo de portafolio) listas para copiar.
- Guía de facilitación para el ritual semanal y la recalibración trimestral.
