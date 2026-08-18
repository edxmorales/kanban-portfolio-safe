# KPS — Kanban de Portafolio con SAFe

**Versión 1.12.0** · Un framework abierto para equipos que reparten personas entre varios proyectos, deuda técnica, soporte y mejoras, con prioridades que cambian cada semana.

> Licencia: CC BY-SA 4.0 — puedes usar, adaptar y redistribuir este framework, incluso comercialmente, siempre que des crédito y mantengas las adaptaciones bajo la misma licencia. Ver [`LICENSE`](./LICENSE).

> 🇬🇧 Reading in English? See [`FRAMEWORK.en.md`](./FRAMEWORK.en.md).

## Tabla de contenido

- [Resumen ejecutivo](#resumen-ejecutivo)
- [0. Diagnóstico 360: el punto de partida obligatorio](#0-diagnóstico-360-el-punto-de-partida-obligatorio)
  - [0.1 Relación con el Diagnóstico 360° de transformación de TI (alcance más amplio)](#01-relación-con-el-diagnóstico-360-de-transformación-de-ti-alcance-más-amplio)
- [1. El problema que resuelve](#1-el-problema-que-resuelve)
- [2. Fundamentos: por qué Kanban + SAFe](#2-fundamentos-por-qué-kanban--safe)
- [3. Los pilares del framework](#3-los-pilares-del-framework)
- [4. Mecánicas propias (lo que ni Kanban ni SAFe traen resuelto)](#4-mecánicas-propias-lo-que-ni-kanban-ni-safe-traen-resuelto)
- [5. Roles y gobierno](#5-roles-y-gobierno)
  - [5.1 Escalamiento y desacuerdos entre roles](#51-escalamiento-y-desacuerdos-entre-roles)
- [6. Cómo se gestionan los equipos](#6-cómo-se-gestionan-los-equipos)
  - [6.1 Cuándo usar freelances y cuándo no: proyecto vs mantenimiento del negocio](#61-cuándo-usar-freelances-y-cuándo-no-proyecto-vs-mantenimiento-del-negocio)
  - [6.2 Dependencias entre flujos de valor](#62-dependencias-entre-flujos-de-valor)
  - [6.3 Onboarding: cuando alguien nuevo entra o rota internamente](#63-onboarding-cuando-alguien-nuevo-entra-o-rota-internamente)
  - [6.4 Iniciativas transversales con ejecución independiente por mercado](#64-iniciativas-transversales-con-ejecución-independiente-por-mercado)
- [7. Cómo entra QA sin convertirse en cuello de botella](#7-cómo-entra-qa-sin-convertirse-en-cuello-de-botella)
- [8. El flujo de infraestructura, de principio a fin](#8-el-flujo-de-infraestructura-de-principio-a-fin)
- [9. Sistema de medición](#9-sistema-de-medición)
  - [9.1 Indicadores de flujo (eficiencia)](#91-indicadores-de-flujo-eficiencia)
  - [9.2 Indicadores de capacidad y carga](#92-indicadores-de-capacidad-y-carga)
  - [9.3 Indicadores de interrupción y costo](#93-indicadores-de-interrupción-y-costo)
  - [9.4 Indicadores de deuda técnica](#94-indicadores-de-deuda-técnica)
  - [9.5 Indicadores de calidad](#95-indicadores-de-calidad)
  - [9.6 Indicadores de predictibilidad](#96-indicadores-de-predictibilidad)
  - [9.7 Puntaje compuesto de eficiencia](#97-puntaje-compuesto-de-eficiencia)
  - [9.8 Cadencia de medición](#98-cadencia-de-medición)
  - [9.9 Indicadores para validar el piloto](#99-indicadores-para-validar-el-piloto)
  - [9.10 Enfoque Lean: eliminación de desperdicio y costo, no solo velocidad](#910-enfoque-lean-eliminación-de-desperdicio-y-costo-no-solo-velocidad)
- [10. Apalancamiento con inteligencia artificial](#10-apalancamiento-con-inteligencia-artificial)
- [11. Hoja de ruta de implementación](#11-hoja-de-ruta-de-implementación)
- [12. Presupuesto y dotación: eficiencia de costos de la operación](#12-presupuesto-y-dotación-eficiencia-de-costos-de-la-operación)
  - [12.1 Dos categorías de costo que compiten por el mismo presupuesto](#121-dos-categorías-de-costo-que-compiten-por-el-mismo-presupuesto)
  - [12.2 Costo de dotación: interno vs. freelance](#122-costo-de-dotación-interno-vs-freelance)
  - [12.3 Categorías mínimas de presupuesto operativo a trackear](#123-categorías-mínimas-de-presupuesto-operativo-a-trackear)
  - [12.4 Cómo el presupuesto se conecta con la capacidad de portafolio](#124-cómo-el-presupuesto-se-conecta-con-la-capacidad-de-portafolio)
  - [12.5 Indicadores de eficiencia de costo (extensión de la sección 9)](#125-indicadores-de-eficiencia-de-costo-extensión-de-la-sección-9)
  - [12.6 Cadencia](#126-cadencia)
- [13. Cómo evoluciona este framework](#13-cómo-evoluciona-este-framework)
- [Anexo: SAFe en profundidad](#anexo-safe-en-profundidad)
- [Anexo: glosario de siglas y términos](#anexo-glosario-de-siglas-y-términos)

---

## Resumen ejecutivo

KPS combina dos piezas a propósito: **Kanban** (flujo continuo y límites de trabajo en curso, a nivel de equipo y de persona) y la **capa de portafolio de SAFe** (Lean Portfolio Management, Portfolio Kanban y priorización WSJF). A eso se suman mecánicas propias para resolver tres problemas que ni Kanban ni SAFe resuelven solos: el conocimiento crítico concentrado en pocas personas, las iniciativas que se congelan en silencio cuando la capacidad se desvía a lo urgente, y la falta de una autoridad clara sobre qué cuenta como "urgente".

No es Scrum: Scrum asume que la prioridad se sostiene durante todo un sprint, y aquí cambia de un día para otro. Tampoco es SAFe completo: SAFe está pensado para 50-125 personas por Tren de Valor, una escala que la mayoría de los equipos que necesitan este framework no tiene ni necesita.

**KPS no se aplica directo sobre un proyecto o una iniciativa.** Antes de tocar cualquier trabajo va primero el [Diagnóstico 360](#0-diagnóstico-360-el-punto-de-partida-obligatorio) (Sección 0) — es el punto de entrada obligatorio, no un anexo opcional. Ningún tablero, límite o rol se instala sin ese diagnóstico completo.

Este documento está pensado para crecer con el uso real. Ver [`CONTRIBUTING.md`](./CONTRIBUTING.md) para proponer cambios y [`CHANGELOG.md`](./CHANGELOG.md) para el historial de versiones.

---

## 0. Diagnóstico 360: el punto de partida obligatorio

**Ninguna regla de este framework se instala a ciegas.** Antes de tocar un tablero, definir un límite de WIP o nombrar un rol, hace falta un diagnóstico de 360 grados del estado real del portafolio — no de lo que se cree que está pasando, sino de lo que muestran los datos. Instalar KPS sin este diagnóstico es adivinar la configuración (qué límite de WIP, qué umbral de Expedite, cuántos flujos de valor) en vez de calibrarla con evidencia.

El diagnóstico 360 revisa cinco ángulos, en este orden:

**1. Capacidad real por persona, no por proyecto.** Para cada persona activa, cuántos ítems tiene en curso ahora mismo, sin importar en cuántas iniciativas distintas estén repartidos. Esto muestra dónde se está concentrando la carga antes de que se vuelva una crisis.

**2. Cumplimiento real de WIP contra el límite declarado.** Si ya existe un límite de trabajo en curso configurado en la herramienta actual, se compara contra la cantidad real de ítems activos. La brecha entre el límite y la realidad ya dice, por sí sola, qué tan bajo control está el sistema hoy.

**3. Estado de cada iniciativa activa.** Cuáles tienen movimiento reciente y cuáles llevan días o semanas sin ningún ítem en curso, sin que nadie lo haya decidido formalmente. Una iniciativa "viva" en el papel pero congelada en la práctica es justo el patrón que KPS busca prevenir.

**4. Estado real de los pull requests y del flujo de código.** Cuántos PRs están abiertos, cuánto tiempo llevan esperando revisión, y si hay señales de que varias personas están tocando la misma zona del sistema al mismo tiempo sin coordinarse.

**5. Actividad real del equipo de QA/automatización.** Si el equipo de calidad tiene su propio historial de commits, PRs o ítems recientes, o si su capacidad real está absorbida en soporte manual que el resto del portafolio no ve.

**El resultado de este diagnóstico no es una opinión: es un inventario con números.** Cuántas personas concentran qué porcentaje del trabajo activo, cuántas iniciativas están de hecho congeladas, cuánto tiempo llevan abiertos los PRs, y si la capacidad de QA existe donde se supone que existe. Esos números son los que después calibran cada pieza del framework — el límite de WIP del pilar 2, el límite de Expedite simultáneos, el piso de capacidad por iniciativa. Sin este paso, cualquier número que se elija es una suposición, no una calibración.

Ver también la sección 0.1 para cómo este diagnóstico se relaciona con un Diagnóstico 360° de TI de alcance más amplio, y el [caso de aplicación 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md) para un ejemplo real de esa relación.

Solo después de completar este diagnóstico se avanza al Paso 1 de la [Hoja de ruta de implementación](#11-hoja-de-ruta-de-implementación).

### 0.1 Relación con el Diagnóstico 360° de transformación de TI (alcance más amplio)

El Diagnóstico 360 de esta sección es una versión especializada y acotada de una metodología más amplia: la que seguiría un Director de TI al llegar a una organización, para evaluar toda la función de tecnología antes de decidir nada. Esa metodología recorre diez frentes — Escuchar, Infraestructura, Aplicaciones, Ciberseguridad, Proyectos y Contratos, Procesos de TI, Presupuesto, Talento Humano, Madurez Digital, y Presentar y Priorizar. La tabla siguiente los detalla, junto con qué tanto de cada uno cubre el Diagnóstico 360 de KPS (los cinco ángulos de la sección anterior):

| # | Frente (diagnóstico 360° de TI, alcance completo) | Qué revisa | ¿Lo cubre el Diagnóstico 360 de KPS? |
|---|---|---|---|
| 1 | Escuchar | Reunirse con Alta Dirección, líderes de negocio, usuarios clave y el equipo de TI, escuchando antes de concluir. | No — KPS asume que ya existe mandato para instalar el framework; no reemplaza las entrevistas iniciales con stakeholders. |
| 2 | Infraestructura | Servidores, redes, comunicaciones, centros de datos, nube, continuidad y estado de activos tecnológicos. | Parcial, de forma indirecta — KPS no diagnostica infraestructura, pero un hallazgo de infraestructura (ej. un techo de capacidad sin autoescalamiento) entra al backlog priorizado de KPS en cuanto se identifica por otro medio. Ver [caso de aplicación 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md). |
| 3 | Aplicaciones | Qué sistemas generan valor, cuáles presentan riesgos, duplicidades, o necesitan evolucionar. | Parcial, de forma indirecta — KPS no evalúa qué aplicaciones generan valor o presentan riesgo, pero si la organización ya cuenta con un inventario interno de aplicaciones de negocio, servicios, desarrollos propios y herramientas operativas, ese inventario alimenta directamente cómo se agrupan los flujos de valor de KPS (pilar 5), igual que ocurre con los frentes 2 y 4. |
| 4 | Ciberseguridad | Vulnerabilidades, accesos, respaldos, continuidad, gestión de incidentes y madurez de seguridad. | El diagnóstico en sí queda fuera de alcance — KPS no audita vulnerabilidades ni controles de seguridad. Pero, como muestra el [caso de aplicación 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md), una vez que ese diagnóstico ya se hizo por otro medio, sus hallazgos se clasifican y priorizan directamente con las clases de servicio y el WSJF de KPS. |
| 5 | Proyectos y Contratos | Alineación estratégica, estado de proyectos, contratos vigentes, riesgos operativos, financieros y legales. | Parcial — solo el estado real de las iniciativas (ángulo 3 del Diagnóstico 360 de KPS); no cubre contratos ni riesgos financieros o legales. |
| 6 | Procesos de TI | Gestión de incidencias, cambios, problemas, activos, continuidad, niveles de servicio y gobierno de TI. | Parcial — solo el flujo de trabajo y de PRs (ángulos 2 y 4 del Diagnóstico 360 de KPS); no cubre incidencias, cambios ni activos como disciplina ITSM completa. |
| 7 | Presupuesto | Inversión actual, su distribución, y el valor que genera cada gasto para la organización. | No, pero relacionado — KPS trata el presupuesto por separado, en la Sección 12, no como parte del diagnóstico inicial. |
| 8 | Talento Humano | Competencias, fortalezas, brechas y oportunidades de desarrollo del equipo. | Parcial — solo la carga de trabajo real por persona (ángulo 1 del Diagnóstico 360 de KPS); no cubre competencias, brechas ni desarrollo. |
| 9 | Madurez Digital | Nivel de digitalización, automatización, uso de datos, innovación, cultura digital y alineación estratégica. | Parcial — solo la porción de automatización y uso de datos que cubre el [Apalancamiento con inteligencia artificial](#10-apalancamiento-con-inteligencia-artificial) (Sección 10); no cubre innovación, cultura digital ni alineación estratégica como disciplina completa. |
| 10 | Presentar y Priorizar | Informe ejecutivo con evidencia, indicadores, riesgos, fortalezas, oportunidades y una hoja de ruta priorizada. | Sí — el inventario con números al final del Diagnóstico 360 de KPS cumple el mismo propósito: alimenta directamente el Paso 0 de la hoja de ruta. |

KPS no intenta cubrir los diez frentes — eso sería un framework de gestión integral de TI, no uno de gestión de flujo de trabajo. Como proceso de diagnóstico, KPS instancia solo una porción específica de esa metodología, sobre todo los frentes 5, 6 y 8. El frente 1 (Escuchar) queda deliberadamente fuera de alcance por completo: KPS no reemplaza las entrevistas iniciales con stakeholders.

Los frentes 2, 3, 4 y 9 son un caso distinto. KPS no los diagnostica — no audita infraestructura, no evalúa aplicaciones, no evalúa vulnerabilidades, no mide madurez digital — pero cuando ese trabajo ya existe por otro medio (un inventario interno, un diagnóstico de seguridad como el del [caso de aplicación 1](./docs/caso-aplicacion-01-diagnostico-seguridad.md)), sus resultados **se integran directo a las mecánicas ya operativas de KPS**: un inventario de aplicaciones o servicios alimenta cómo se agrupan los flujos de valor (pilar 5), los hallazgos de infraestructura o seguridad entran al backlog priorizado con WSJF y clases de servicio, y la automatización o el uso de datos entran por la Sección 10. La distinción importa: KPS no reemplaza esos diagnósticos, pero tampoco los ignora una vez que existen.

**Cuándo usar cada uno:** si el objetivo es instalar KPS sobre un equipo o portafolio que ya tiene sponsor y mandato, el Diagnóstico 360 de la sección anterior basta. Si el objetivo es una transformación de TI completa — evaluar toda la función de tecnología de una organización, no solo cómo fluye el trabajo dentro de un equipo — los cinco ángulos de KPS se quedan cortos por diseño, y hace falta recorrer los diez frentes antes (o en paralelo) de decidir si KPS es siquiera la herramienta correcta para la capa de flujo de trabajo.

---

## 1. El problema que resuelve

Cada semana cambian las prioridades, entra trabajo nuevo sin parar, y aun así la sensación es la misma: se saca trabajo del atasco y llega más atasco. Hay iniciativas que avanzan y otras que se quedan congeladas sin que nadie lo haya decidido formalmente. Los pull requests se acumulan antes de cada paso a producción. Las pruebas parecen siempre atrasadas respecto al desarrollo.

Esto pasa cuando se mezclan cuatro tipos de trabajo muy distintos — proyectos nuevos, deuda técnica, soporte/incidentes y mejoras — en el mismo equipo, sin reglas explícitas sobre cómo compiten por la atención de las mismas personas. Y pasa también cuando distintas iniciativas comparten el mismo grupo de personas sin ninguna vista conjunta de cuánta capacidad tiene cada quien.

## 2. Fundamentos: por qué Kanban + SAFe

Kanban ordena el flujo dentro de un equipo: visualiza el trabajo, limita cuánto puede estar en curso a la vez, y usa clases de servicio para que no todo compita en igualdad de condiciones. Pero Kanban no dice nada sobre qué hacer cuando la misma persona está repartida entre iniciativas que no se ven entre sí.

Ahí entra la capa de portafolio de SAFe: una sola vista de todas las iniciativas (Portfolio Kanban), una lógica de priorización con números detrás (WSJF) en vez de la opinión de quien habla más fuerte, y el principio de gestionar capacidad por flujo de valor en vez de proyecto por proyecto (Lean Portfolio Management).

KPS toma exactamente esas dos piezas y deja fuera toda la ceremonia de programa y coordinación entre Trenes de Valor que SAFe agrega para escalas de cientos de personas. Ver el [Anexo: SAFe en profundidad](#anexo-safe-en-profundidad) para el detalle de competencias, configuraciones y principios, y qué de todo eso KPS decide no adoptar.

## 3. Los pilares del framework

1. **Una sola vista de capacidad, no un tablero por proyecto.** Equivale al Portfolio Kanban de SAFe: todas las iniciativas en una sola vista, para ver cuánto tiene encima cada persona sin importar a cuál iniciativa pertenece cada ítem.
2. **Límite de trabajo en curso por persona, no solo por equipo.** Un equipo puede estar "dentro del límite" mientras dos personas cargan la mitad del trabajo. La regla real es un tope individual (1-2 ítems activos): cuando alguien lo alcanza, lo siguiente espera, se reasigna, o se decide conscientemente pausar algo suyo.
3. **Clases de servicio con comportamiento, priorizadas con WSJF.** Expedite, Fecha fija, Estándar e Intangible, cada una con reglas propias de límite y de orden. Qué entra primero se decide con costo de demora dividido entre tamaño del trabajo, no con intuición.
4. **Piso de capacidad para toda iniciativa activa (Lean Portfolio Management).** Ninguna iniciativa que siga viva puede quedar en cero personas de forma implícita. Si hay que desviar capacidad a una emergencia, sale de un pool flexible reservado para eso.
5. **Flujos de valor en vez de proyectos aislados.** Las iniciativas se agrupan por el valor de negocio que entregan, no por nombre de proyecto, para que mover capacidad dentro del mismo flujo no se sienta como abandonar algo.
6. **Ritual semanal con una regla de oro.** El triage semanal reordena lo que no ha empezado. Lo que ya está en curso no se toca, salvo una emergencia real de clase Expedite, y esa excepción se registra como interrupción.
7. **Recalibración trimestral corta.** Medio día cada trimestre para ajustar pisos de capacidad y límites con los datos acumulados — versión reducida del PI Planning de SAFe.

## 4. Mecánicas propias (lo que ni Kanban ni SAFe traen resuelto)

- **Costo de interrupción medido en horas:** cada interrupción de clase Expedite sobre un trabajo en curso se estima y se acumula en un reporte periódico, para que el costo de "lo urgente" deje de ser invisible.
- **Guardia rotativa ("bombero de la semana"):** un rol semanal rotativo absorbe lo Expedite, en vez de que siempre recaiga sobre las mismas 1-2 personas con más conocimiento. Con el tiempo, esto obliga a que ese conocimiento se reparta.
- **Interés creciente sobre la deuda técnica:** cada ítem de deuda acumula un puntaje que sube semana a semana sin atenderse, para que competir contra lo urgente del día deje de ser una batalla perdida de antemano.
- **Autoridad explícita para declarar Expedite:** una persona con nombre y rol definido aprueba esa clasificación. Sin esa aprobación, el ítem entra como Estándar, aunque alguien insista en que es urgente.
- **Visibilidad radical:** la carga de cada persona y el estado de cada iniciativa son visibles para toda la organización, no solo para quien lidera. La presión social sostiene las reglas mejor que cualquier auditoría de arriba hacia abajo.

## 5. Roles y gobierno

KPS no necesita una estructura de roles pesada, pero sí necesita que cada regla tenga un dueño con nombre. Sin eso, las reglas se ignoran bajo presión — exactamente el problema que KPS busca resolver. Y necesita, además, que ese dueño nunca sea un punto único de falla: por eso cada rol de esta tabla tiene también un respaldo nombrado explícitamente.

| Rol | Responsabilidad | Autoridad | Respaldo |
|---|---|---|---|
| **Responsable de Flujo de Portafolio** | Mantiene la vista única de capacidad actualizada y decide qué pasa cuando alguien llega a su tope de WIP | Puede pausar, reasignar o rechazar la entrada de un nuevo ítem a una persona saturada | Una segunda persona nombrada puede tomar la misma decisión si el titular no está disponible — sin esto, este rol tendría el mismo bus factor que el framework busca eliminar en el resto del equipo |
| **Aprobador de Clase de Servicio** | Evalúa y aprueba (o rechaza) que un ítem entre como Expedite | Es la única autoridad que puede etiquetar algo como Expedite | Respaldo nombrado con la misma autoridad — este rol nunca queda sin cobertura, ni un día, porque lo urgente no espera a que alguien vuelva de vacaciones |
| **Facilitador del Ritual Semanal** | Corre el triage semanal, hace cumplir la regla de no tocar lo que ya está en curso, y verifica que ningún ítem entre a desarrollo sin cumplir la Definición de Listo (sección 7) | Puede vetar una reasignación que rompa la regla de protección del trabajo en curso, y devolver a refinamiento cualquier ítem que no cumpla la Definición de Listo | Cualquier otro facilitador entrenado en la regla de protección del ritual puede cubrir una semana puntual |
| **Líder de Flujo de Valor** | Dueño de una agrupación de iniciativas por valor de negocio; negocia capacidad con el Responsable de Flujo de Portafolio; resuelve el primer nivel de desacuerdos dentro de su flujo (sección 5.1) | Decide prioridades dentro de su flujo de valor, no entre flujos distintos | Respaldo nombrado dentro del mismo flujo de valor, con suficiente contexto para negociar capacidad sin empezar de cero |
| **Representante de Valor de Negocio** | Estima y sostiene el costo de demora (Cost of Delay) de las iniciativas de su flujo, insumo directo del WSJF; valida que la priorización siga reflejando lo que el negocio o el cliente necesita | Es la única fuente aceptada para el componente de valor de negocio del WSJF — sin su estimación, un ítem se prioriza con una aproximación, no con el WSJF completo | Respaldo nombrado con visibilidad directa del negocio o del cliente, no solo del backlog técnico |
| **Guardia Rotativa (Firefighter)** | Absorbe lo Expedite durante su semana de turno | Puede reclamar cualquier ítem Expedite sin pasar por la fila normal de asignación | La rotación semanal es, en sí misma, el mecanismo de respaldo — nadie depende de una sola persona para atender lo urgente |
| **Dueño de Calidad del Flujo** | Sostiene el límite de WIP de la etapa de QA y la cobertura de pruebas automatizadas | Puede bloquear el paso de un ítem a "Listo para desplegar" si no cumple la Definición de Hecho | Respaldo nombrado dentro del equipo de QA/automatización con la misma autoridad de bloqueo |

Ninguno de estos roles necesita ser una dedicación de tiempo completo ni un cargo nuevo en el organigrama. Pueden (y suelen) ser sombreros que ya usan personas del equipo — incluido el Representante de Valor de Negocio, que en la mayoría de los casos ya existe en la organización bajo otro nombre (product owner, dueño de producto, patrocinador). Lo único no negociable es que quién trae puesto cada sombrero, y quién es su respaldo, quede explícito y visible para todo el equipo (pilar de visibilidad radical, sección 4).

### 5.1 Escalamiento y desacuerdos entre roles

Ninguna estructura de roles evita del todo el desacuerdo. Lo que KPS necesita es que el desacuerdo tenga una ruta conocida, en vez de resolverse por quien insiste más o por jerarquía informal:

1. **Nivel 1 — dentro de un mismo flujo de valor** (ej. el Aprobador de Clase de Servicio rechaza un Expedite que alguien insiste en pedir, o hay disputa sobre una estimación de WSJF). Lo resuelve el Líder de Flujo de Valor de esa iniciativa, con la autoridad ya definida en la tabla de roles.
2. **Nivel 2 — entre un flujo de valor y la vista de portafolio** (ej. una reasignación de capacidad que un Líder de Flujo de Valor no acepta, o una dependencia entre flujos que no se alinea — ver sección 6.2). Se lleva como punto explícito de agenda al ritual semanal; no se resuelve por fuera de él ni por mensajes informales.
3. **Nivel 3 — desacuerdo que no se resolvió en el ritual semanal** (ej. una disputa de prioridad estratégica entre dos flujos de valor). Se escala a la recalibración trimestral y se resuelve con los datos del sistema de medición (sección 9) como evidencia — nunca como una opinión más entre varias.

**Regla de cierre:** mientras un desacuerdo está en curso, se mantiene intacta la regla de protección del trabajo ya iniciado (pilar 6). Ningún desacuerdo sin resolver es excusa para tocar algo que ya está en curso.

## 6. Cómo se gestionan los equipos

KPS organiza a las personas alrededor de **flujos de valor**, no de proyectos aislados con equipos fijos. Dentro de cada flujo de valor conviven roles de front, back, full stack y QA. El objetivo no es que cada persona pertenezca exclusivamente a un flujo para siempre, sino que su carga activa (WIP) nunca exceda su tope individual, sin importar de cuántos flujos venga ese trabajo.

Los equipos que dan soporte a todos los flujos por igual — automatización de QA, DevSecOps, plataforma — se tratan como un **pool habilitante compartido**, no como un proyecto más con su propio tablero aislado. Su capacidad entra en la misma vista única de portafolio que la de cualquier flujo de valor, precisamente para que un equipo de soporte no desaparezca de la vista general cuando su trabajo no se refleja en ningún tablero de proyecto.

Cuando una persona se mueve entre flujos de valor — algo que va a seguir pasando, y está bien que pase — ese movimiento se registra en la vista única de capacidad el mismo día, no al final de la semana. Así el Responsable de Flujo de Portafolio siempre sabe, en tiempo real, quién tiene espacio y quién no.

### 6.1 Cuándo usar freelances y cuándo no: proyecto vs mantenimiento del negocio

No todo el trabajo debería resolverse con el mismo tipo de dotación. KPS distingue explícitamente dos naturalezas de trabajo para decidir si conviene personal freelance/por contrato o personal interno permanente:

**Trabajo tipo proyecto (apto para freelance).** Tiene alcance definido, fecha de entrega, y una vez entregado, termina: se ejecuta, se entrega, y el contrato se cierra. Encaja naturalmente con las clases de servicio Fecha fija y Estándar. Ejemplos: construir un módulo nuevo con requerimientos ya definidos, una migración puntual, una integración con un proveedor específico.

**Trabajo de mantenimiento del negocio (debe quedarse interno).** Soporte, incidentes, deuda técnica continua y mejoras incrementales sobre un sistema vivo. Este trabajo requiere continuidad de conocimiento y disponibilidad rápida — es justo el tipo de trabajo donde un freelance que termina su contrato y se va empeora el bus factor en vez de mejorarlo, porque el conocimiento del sistema se va con la persona.

**Criterios para decidir en qué categoría cae una iniciativa:**

- ¿Tiene una fecha de fin natural, después de la cual nadie necesita seguir tocándola? → candidata a freelance.
- ¿Requiere soporte continuo después de su lanzamiento? → debe quedarse con personal interno.
- ¿Depende de conocimiento tácito del negocio que tomaría meses transferir? → personal interno.
- ¿Es parte del "core" de un flujo de valor permanente, o es una iniciativa puntual dentro de él? → lo permanente se queda interno; lo puntual puede salir a freelance.

**Reglas operativas cuando se usa freelance:**

- La capacidad de un freelance entra en la misma vista única de capacidad que el resto del portafolio (pilar 1), marcada explícitamente con su fecha de fin de contrato — así el Responsable de Flujo de Portafolio nunca construye una dependencia permanente sobre alguien que va a irse en una fecha conocida.
- Todo freelance entrega documentación de lo construido como parte de su Definición de Hecho, no como algo opcional de última hora — esto es lo que evita que el conocimiento salga por la puerta junto con la persona (ver también el apalancamiento con IA para generar esta documentación en la sección 10).
- Ningún ítem de la clase de servicio Intangible (deuda técnica) ni Expedite (incidentes de seguridad) se asigna a un freelance sin una razón explícita — por su naturaleza, ambas clases requieren continuidad y conocimiento profundo del sistema.

### 6.2 Dependencias entre flujos de valor

Un flujo de valor casi nunca es una isla: a veces una iniciativa de un flujo necesita algo que solo otro flujo puede entregar (un endpoint, una migración compartida, una decisión de arquitectura común). KPS no adopta la coordinación de programa que SAFe usa entre Trenes de Valor, porque asume una escala que este framework no tiene — pero sí necesita una regla ligera para que las dependencias no se descubran cuando ya bloquearon algo.

- **Toda dependencia se declara en el refinamiento, no después.** Es parte de la Definición de Listo (sección 7): un ítem que depende de otro flujo de valor no está "listo" hasta que esa dependencia queda escrita y visible.
- **La dependencia vive en la vista única de capacidad (pilar 1),** marcada con el flujo de valor del que depende, no solo en el tablero del flujo que la originó.
- **Un desacuerdo sobre una dependencia entre dos Líderes de Flujo de Valor** sigue el nivel 2 del escalamiento (sección 5.1): pasa al ritual semanal ante el Responsable de Flujo de Portafolio, no se resuelve de forma bilateral e informal.
- **Indicador de seguimiento (extiende la sección 9.2):** número de ítems bloqueados por una dependencia de otro flujo, y tiempo que llevan bloqueados. Si este número crece de forma sostenida, es evidencia de que los flujos de valor están mal agrupados (pilar 5) y deberían redefinirse — no de que hace falta más presión sobre las personas.

### 6.3 Onboarding: cuando alguien nuevo entra o rota internamente

La sección 6.1 ya cubre qué pasa cuando un freelance cierra su contrato. Esta sección cubre el caso más frecuente: alguien nuevo entra al equipo, o alguien interno rota de un flujo de valor a otro — algo que la sección 6 ya reconoce como normal y esperado.

**Al entrar una persona nueva (interna o freelance) a un flujo de valor:**

- Recibe, desde el primer día, un tope de WIP reducido (la mitad del estándar del equipo) durante sus primeras semanas, marcado explícitamente en la vista única de capacidad — no el mismo límite que alguien con contexto ya acumulado.
- El Líder de Flujo de Valor designa, de forma informal y sin crear un rol nuevo, a alguien del flujo como punto de referencia de contexto durante ese período.
- Tiene acceso, desde el primer día, a la documentación generada por el apalancamiento de IA (sección 10) y a la dejada por cualquier freelance saliente (sección 6.1) — el conocimiento ya documentado no debería depender de que alguien se lo repita en persona.

**Al rotar una persona interna de un flujo de valor a otro:**

- Antes de salir de su flujo actual, documenta lo que solo ella sabe del trabajo en curso que deja — el mismo principio de la Definición de Hecho aplicado al freelance en 6.1, extendido también a la rotación interna, no solo a los cierres de contrato.
- El Índice de Concentración (9.2) se revisa antes y después de cada rotación: mover a la persona que más WIP concentra sin transferir su conocimiento primero no resuelve el bus factor, solo lo traslada a otro flujo de valor.

### 6.4 Iniciativas transversales con ejecución independiente por mercado

Es distinto que un flujo de valor dependa de otro (sección 6.2) a que una misma capacidad — la misma iniciativa, el mismo build — deba desplegarse en varios mercados, segmentos o clientes que pueden avanzar, bloquearse o completarse sin depender entre sí. Tratar esto como una sola tarjeta agregada produce un problema concreto: en el momento en que un mercado se bloquea, la tarjeta completa se ve "Bloqueada" aunque el resto ya esté en producción, lo que oculta el avance real y arriesga que la persona asignada quede retenida en un ítem parado en vez de liberarse hacia el mercado que sí puede avanzar.

**Regla:** cuando una iniciativa transversal tiene mercados que pueden moverse de forma independiente por el flujo de trabajo, cada mercado es su propia tarjeta en la vista única de capacidad (pilar 1) — nunca una sola tarjeta que agregue el estado de todos.

- **Un nombre base compartido identifica la familia** (ej. "Iniciativa — Mercado"), para que la iniciativa no se pierda de vista como conjunto aunque cada mercado tenga su propia tarjeta.
- **El bloqueo de un mercado nunca ocupa el tope de WIP individual (pilar 2) de la persona asignada a otro.** Si el mercado A se bloquea, la persona queda libre para tomar el mercado B de la misma familia (o cualquier otro ítem dentro de su flujo de valor) mientras el bloqueo de A se resuelve.
- **El criterio para decidir si conviene dividir en tarjetas por mercado**, y no dejarlo en una sola: ¿los mercados pueden tener un estado distinto entre sí en algún momento del trabajo (uno certificado y otro no, uno con regulación local propia, uno con fecha límite distinta)? Si la respuesta es sí, se divide. Si los mercados siempre se mueven juntos, con el mismo equipo y la misma fecha (se construye una vez y se despliega a todos al mismo tiempo), una sola tarjeta es suficiente — el Tamaño de esa tarjeta simplemente refleja que cubre varios mercados a la vez.
- **Cuándo dividir, y cuándo todavía no:** mientras la iniciativa sigue en validación (POC, prueba de concepto, piloto interno) y no se ha decidido si se lanza ni a qué mercados, se mantiene como una sola tarjeta — dividirla antes de esa decisión multiplicaría filas sobre algo que ni siquiera se sabe si va a existir. La división ocurre en el momento en que la iniciativa pasa de "se está evaluando" a "se aprueba y arranca la ejecución", porque es justo ahí cuando los mercados empiezan a poder tener estados distintos entre sí (uno arranca, otro no, uno se bloquea). Antes de ese punto, el ítem vive en la clase de servicio que le corresponda a una POC (normalmente Intangible o Estándar), no como iniciativa transversal todavía.
- **La iniciativa como conjunto se considera completa cuando todos sus mercados llegan a "Completado"**, no antes — esto se verifica filtrando por el nombre base en la vista única de capacidad, sin necesitar una tarjeta adicional que la represente.

**Indicador de seguimiento (extiende la sección 9.1):** % de mercados en "Completado" sobre el total de mercados objetivo, por iniciativa transversal — así el semáforo compuesto (9.7) no se ensucia por un bloqueo aislado en un solo mercado cuando el resto de la iniciativa avanza con normalidad.

## 7. Cómo entra QA sin convertirse en cuello de botella

El error más común es tratar a QA como una compuerta al final del proceso, separada del resto del flujo. En KPS, QA es una etapa más del mismo tablero, con su propio límite de trabajo en curso — no un proyecto aparte con su propio backlog invisible.

El flujo de un ítem, de principio a fin:

`Backlog clasificado → Refinamiento (criterios de aceptación y de prueba definidos) → En desarrollo (WIP por persona) → Revisión de código / PR (WIP por revisor) → QA (WIP propio) → Listo para desplegar → Producción`

Tres reglas hacen que esto funcione sin que QA se convierta en el atasco:

**Primero, QA entra desde el refinamiento, no al final.** Los criterios de aceptación y los casos de prueba se definen antes de que el ítem entre a desarrollo, no después de que el código ya esté listo. Esto es "shift-left": QA participa en decidir qué significa "terminado" desde el primer día, en vez de descubrir al final que falta cubrir un caso.

**Segundo, la capacidad de QA es parte de la misma vista de portafolio, no un proyecto aparte.** Si el equipo de automatización de QA tiene su propio backlog separado del resto del trabajo, su carga real se vuelve invisible para quien gestiona el portafolio, y termina absorbido en soporte manual sin que nadie lo note hasta que las pruebas automatizadas dejan de avanzar.

**Tercero, nada pasa a "Listo para desplegar" sin cumplir la Definición de Hecho, y esa definición incluye pruebas.** Definición de Hecho mínima: código fusionado, pruebas automatizadas pasando, casos de aceptación validados por QA, y un plan de monitoreo post-despliegue si aplica. El Dueño de Calidad del Flujo tiene autoridad para bloquear el paso si algo de esto falta, así la presión de "ya está casi listo" no empuja algo a producción sin haber pasado por QA de verdad.

**La Definición de Hecho tiene su contraparte al inicio: la Definición de Listo, en concreto.** Un ítem no entra a "En desarrollo" hasta tener, como mínimo: criterios de aceptación escritos y verificables, casos de prueba definidos (no solo mencionados) por QA, cualquier dependencia de otro flujo de valor declarada explícitamente (sección 6.2), y una clase de servicio ya aprobada por el Aprobador de Clase de Servicio (sección 5). El Facilitador del Ritual Semanal tiene autoridad para devolver a refinamiento cualquier ítem que no cumpla esto — el mismo tipo de autoridad con el que el Dueño de Calidad del Flujo bloquea la salida a producción, pero en la entrada.

## 8. El flujo de infraestructura, de principio a fin

El objetivo de esta sección es que llegar a producción deje de sentirse como una sorpresa. Cada etapa tiene una regla concreta:

**Antes de programar: la señal de "estoy tocando esto".** Antes de crear una rama, se anuncia qué módulo o dominio se va a modificar. Esto evita que varias personas toquen la misma zona del sistema al mismo tiempo sin saberlo hasta el momento de fusionar.

**Estrategia de ramas.** Ramas de vida corta (1-3 días máximo) o desarrollo directo sobre la rama principal protegida por feature flags. Nunca ramas de larga duración que acumulan cambios y se vuelven difíciles de fusionar.

**Política de pull requests.** Límite de PRs abiertos por persona (1-2, coherente con el límite de WIP), al menos un revisor obligatorio, controles automáticos (build, pruebas unitarias, análisis estático de seguridad) que deben pasar antes de que un humano revise, y un tamaño de diferencia recomendado (por ejemplo, bajo ~400 líneas) para que las revisiones sean rápidas y no se acumulen.

**Pipeline de integración continua.** Build → pruebas unitarias → análisis estático/seguridad → despliegue automático a un ambiente de prueba → validación de QA (manual y automatizada) → aprobación → fusión a la rama de release.

**Ambientes y promoción.** Desarrollo → Prueba/QA → Staging (lo más parecido posible a producción) → Producción, con criterios explícitos de qué se necesita para pasar de un ambiente al siguiente. Nunca una promoción "de facto" porque ya se acabó el tiempo.

**Feature flags para desacoplar el merge del release.** El código puede fusionarse a la rama principal sin estar activo para los usuarios, lo que permite integración continua real sin esperar a que todo el paquete de la semana esté listo al mismo tiempo.

**Plan de rollback definido antes de desplegar, no improvisado durante el incidente.** Cada despliegue debe tener claro cómo se revierte (apagar el feature flag, redesplegar la versión anterior) antes de salir a producción, no cuando ya está fallando.

**Ventana de observación post-despliegue.** Un período definido después de cada despliegue donde el equipo vigila activamente métricas de error y alertas antes de dar el despliegue por completamente cerrado. Esta es la etapa que más elimina las "sorpresas" en producción.

## 9. Sistema de medición

Principio rector de esta sección: **lo que no se mide no mejora ni se ve.** Por eso ningún indicador de KPS se mide una sola vez ni queda a discreción de si alguien se acuerda. Todos entran en el mismo ciclo diario/semanal/mensual/trimestral ya definido en el resto del framework, y todos apuntan a un solo objetivo: hacer visible la eficiencia real del sistema, no solo qué tan ocupada se ve la gente.

### 9.1 Indicadores de flujo (eficiencia)

- **Lead time y cycle time, por clase de servicio.** Un ítem Expedite y uno Estándar no deberían medirse juntos: mezclar sus tiempos oculta si el sistema realmente prioriza lo que dice priorizar.
- **Throughput:** ítems completados por semana, por flujo de valor.
- **Eficiencia de flujo (Flow Efficiency):** tiempo en que un ítem estuvo realmente siendo trabajado, dividido entre el tiempo total que pasó en el sistema, expresado en porcentaje. Este es el indicador central de eficiencia real: casi siempre revela que la mayor parte del tiempo el ítem estuvo esperando (en cola de revisión de código, esperando QA) y no siendo trabajado. Es el número que más le importa a quien pregunta "¿por qué esto tarda tanto si nadie está de brazos cruzados?".

### 9.2 Indicadores de capacidad y carga

- **% de cumplimiento de WIP por persona:** proporción de días en que cada persona estuvo dentro de su tope individual, no por encima.
- **Índice de concentración:** qué porcentaje del WIP total del portafolio sostienen las dos personas con más carga. Este número vuelve objetivo un patrón que de otra forma solo se percibe de forma anecdótica: si dos personas concentran un 40% o más del trabajo activo, hay un riesgo de bus factor real, con un número detrás y no solo una impresión.
- **Distribución de capacidad entre flujos de valor**, comparada contra el piso mínimo acordado para cada uno.

### 9.3 Indicadores de interrupción y costo

- **Ítems Expedite abiertos simultáneamente**, comparado contra el límite acordado.
- **Costo de interrupción acumulado**, en horas estimadas.
- **% de interrupciones que, revisadas después, realmente ameritaban ser Expedite.** Este número permite calibrar con evidencia si la autoridad de clasificación está siendo demasiado permisiva.

### 9.4 Indicadores de deuda técnica

- **Puntaje acumulado de deuda pendiente**, y su tendencia en el tiempo (¿sube, baja, se estanca?).
- **% de la capacidad semanal realmente destinada a deuda técnica**, comparado contra la cuota acordada.

### 9.5 Indicadores de calidad

- **Defectos escapados a producción**, por período.
- **Cobertura de pruebas automatizadas**, y su tendencia.
- **% de ítems que regresan de QA a desarrollo (rework).** Un indicador alto aquí suele señalar que el shift-left de la sección 7 no se está cumpliendo de verdad.

### 9.6 Indicadores de predictibilidad

- **% de ítems de clase Fecha fija entregados a tiempo.**
- **Varianza del lead time:** un sistema puede ser rápido en promedio y aun así impredecible. Esta métrica mide qué tan confiable es una fecha estimada, no solo qué tan rápido va el promedio.

### 9.7 Puntaje compuesto de eficiencia

Para tener un solo número que se pueda ver de un vistazo (semáforo verde/amarillo/rojo), se recomienda combinar cuatro indicadores clave: Eficiencia de flujo, % de cumplimiento de WIP, Índice de concentración, y % de entrega a tiempo en Fecha fija. Ningún indicador individual cuenta la historia completa. El puntaje compuesto es lo que se revisa primero en el ritual semanal, y cada indicador individual es a dónde se va a investigar cuando el compuesto empeora.

### 9.8 Cadencia de medición

- **Diaria:** captura silenciosa de los datos base (ya cubierto en la operación del PM/agente de seguimiento), sin reporte salvo alerta.
- **Semanal:** refresco completo del dashboard y revisión en el ritual semanal.
- **Mensual:** revisión de tendencias y recalibración de umbrales (límite de Expedite, días de congelamiento considerados alerta).
- **Trimestral:** recalibración completa junto con la sesión de portafolio del paso 6 de la hoja de ruta.

### 9.9 Indicadores para validar el piloto

Estos son los que convierten "creemos que mejoró" en evidencia real:

| Indicador | Antes del piloto | Después del piloto | Flujo de control |
|---|---|---|---|
| Lead time promedio | | | |
| Eficiencia de flujo (%) | | | |
| % cumplimiento de WIP | | | |
| Índice de concentración | | | |
| Iniciativas con 0 ítems activos > 5 días hábiles | | | |
| PRs abiertos > 2 días | | | |
| % entrega a tiempo (Fecha fija) | | | |

Esta tabla, llenada con datos reales antes y después, y comparada contra un flujo de valor que no aplicó KPS en paralelo, es el artefacto concreto que separa "framework propuesto" de "metodología con evidencia" — y es exactamente lo que se documenta como caso de estudio para la próxima versión del framework.

**Criterio de decisión (go/no-go) al cerrar el piloto:**

- **Se expande a más flujos de valor** si, comparado contra el flujo de control, al menos tres de los cuatro indicadores del puntaje compuesto (9.7) mejoran de forma sostenida (varias semanas, no una sola buena semana) y ninguno empeora de forma sostenida.
- **Se ajusta y se repite el piloto en el mismo flujo de valor** si solo uno o dos indicadores mejoran. Se recalibran los parámetros más probables (límite de WIP, umbral de Expedite, agrupación de flujos de valor) antes de intentar expandir.
- **Se documenta como aprendizaje negativo en el CHANGELOG** si ningún indicador mejora. Que un piloto no funcione en un contexto específico es información válida para la siguiente versión del framework, no un fracaso que ocultar.

### 9.10 Enfoque Lean: eliminación de desperdicio y costo, no solo velocidad

Medir por medir no mejora nada si no se conecta con eliminar desperdicio real. Cada indicador de esta sección apunta a un desperdicio concreto del pensamiento Lean:

| Desperdicio Lean | Cómo se ve en este contexto | Indicador que lo expone |
|---|---|---|
| Espera | Ítems detenidos en cola de revisión de código o de QA | Eficiencia de flujo baja; antigüedad en esas columnas |
| Exceso de trabajo en curso | Más ítems activos de los que el sistema puede sostener | % de cumplimiento de WIP |
| Retrabajo/defectos | Ítems que rebotan de QA a desarrollo | % de rework; defectos escapados |
| Sobreprocesamiento | Ceremonia o aprobación innecesaria para trabajo simple | Revisar si el tiempo de ciclo de ítems Estándar es desproporcionado frente a su tamaño |
| Conocimiento no transferido | Una persona concentra trabajo que nadie más puede tomar | Índice de concentración |
| Movimiento/handoffs | Un ítem pasa por manos o aprobaciones que no agregan valor | Contar cuántas manos toca un ítem entre Backlog y Producción |

El objetivo de fondo de todo el sistema de medición no es "ir más rápido" a cualquier costo, sino **exponer dónde se pierde tiempo y dinero sin agregar valor**, para poder eliminarlo con evidencia. Eficiencia operativa real, no solo la sensación de estar ocupados.

## 10. Apalancamiento con inteligencia artificial

KPS está diseñado para apoyarse en herramientas de IA en los puntos donde generan la mayor reducción de desperdicio y costo operativo, no como un agregado cosmético sino integradas a las mecánicas ya descritas:

- **Captura y reporte del flujo diario/semanal.** Un asistente de IA puede leer las actualizaciones diarias del equipo (o una transcripción de la reunión de seguimiento) y mantener actualizada la vista única de capacidad sin que nadie tenga que digitarlo dos veces, dejando el reporte semanal armado automáticamente a partir de esos datos.
- **Sugerencia de clase de servicio.** Al entrar un ítem nuevo, un asistente de IA puede proponer si suena a Expedite, Fecha fija, Estándar o Intangible según su descripción. El Aprobador de Clase de Servicio sigue siendo quien decide, pero no parte de cero.
- **Apoyo a la estimación de WSJF.** Un asistente de IA puede proponer un costo de demora y un tamaño estimado basándose en ítems históricos similares, para que la priorización tenga un punto de partida objetivo en vez de depender solo de la intuición de quien estima.
- **Generación de documentación para reducir bus factor.** Esto conecta directo con la sección 6.1: un asistente de IA puede ayudar a transformar el conocimiento tácito de las personas que más saben (o de un freelance antes de que termine su contrato) en documentación real, a partir de código, commits y explicaciones grabadas, reduciendo el costo de transferencia de conocimiento que hoy se pierde.
- **Apoyo a QA:** generación de casos de prueba y de scaffolding de pruebas automatizadas a partir de los criterios de aceptación definidos en el refinamiento, para aliviar la presión sobre el equipo de automatización sin saltarse el shift-left de la sección 7.
- **Alertas de eficiencia:** un asistente de IA puede vigilar continuamente los indicadores de la sección 9 y avisar apenas alguno cruce su umbral (WIP excedido, iniciativa congelada, Expedite por encima del límite), en vez de esperar al ritual semanal para descubrirlo.

En todos los casos, la IA acelera la ejecución de las reglas que ya definió el framework. Nunca reemplaza a quien tiene la autoridad de decisión (Responsable de Flujo de Portafolio, Aprobador de Clase de Servicio, Dueño de Calidad del Flujo). Esa distinción es la que evita que "apalancado con IA" se convierta en una caja negra que nadie entiende ni puede auditar.

## 11. Hoja de ruta de implementación

0. **Completar el [Diagnóstico 360](#0-diagnóstico-360-el-punto-de-partida-obligatorio).** Sin este paso, los siguientes son configuración a ciegas.
1. **Mapear el vocabulario.** Dejar por escrito las equivalencias con SAFe para que cualquiera que lo conozca reconozca la lógica.
2. **Definir por escrito qué de SAFe no se adopta.** Sin Trenes de Valor formales, sin planificación de varios días.
3. **Instalar la priorización con WSJF simplificado** en vez de la discusión informal semanal.
4. **Definir los flujos de valor** del portafolio, agrupando iniciativas por el valor de negocio que entregan.
5. **Nombrar cada rol de gobierno con su respaldo** (sección 5) y designar quién ejerce el Representante de Valor de Negocio en cada flujo. Sin esto, el WSJF del paso 3 no tiene quién le dé el número de costo de demora.
6. **Reemplazar la planificación pesada** por un espacio trimestral corto de recalibración.
7. **Instalar las mecánicas propias:** guardia rotativa, costo de interrupción, interés de deuda técnica, autoridad de clasificación, visibilidad radical.
8. **Piloto acotado de 4-6 semanas** en dos flujos de valor, con el criterio de decisión de la sección 9.9 ya acordado desde antes de empezar. "Qué cuenta como éxito" no se define después de ver los resultados.

## 12. Presupuesto y dotación: eficiencia de costos de la operación

Ningún sistema de flujo es completo si no conecta con lo que cuesta sostenerlo. Esta sección no reemplaza el proceso financiero de la organización: declara cómo el presupuesto y la dotación se conectan con las reglas de capacidad ya definidas en el resto del framework, para que la eficiencia no se mida solo en velocidad sino también en costo.

### 12.1 Dos categorías de costo que compiten por el mismo presupuesto

Toda la capacidad del equipo se reparte, lo declare alguien formalmente o no, entre dos tipos de gasto:

- **Mantener el negocio andando (run the business):** soporte, incidentes, mantenimiento correctivo y la cuota de deuda técnica. No genera valor nuevo, pero su ausencia genera pérdida — un incidente no atendido o una deuda no pagada cuesta más después que ahora.
- **Cambiar el negocio (change the business):** proyectos nuevos, mejoras e iniciativas estratégicas. Es el gasto que sí genera valor incremental visible.

**Regla de gobierno:** el porcentaje de capacidad (y por tanto de presupuesto de personas) destinado a cada categoría se declara como un número explícito, revisado en la recalibración trimestral, no se deduce después de que ya se gastó. El piso de capacidad por iniciativa (pilar 3) y la cuota de deuda técnica (9.4/9.10) son la forma en que esta regla ya opera en el día a día; esta sección solo la hace visible también en términos de presupuesto.

### 12.2 Costo de dotación: interno vs. freelance

Retomando los criterios de la sección 6.1, la comparación de costo entre personal interno y freelance no es solo la tarifa por hora:

- **Costo cargado interno:** salario, prestaciones y gastos generales. Capacidad estable, disponible también para trabajo de mantenimiento del negocio y para el conocimiento tácito que no se puede subcontratar.
- **Costo freelance:** normalmente más bajo por hora facturada, pero con un costo oculto que hay que sumar explícitamente: la transferencia de conocimiento al cierre del contrato (ya exigida como regla en 6.1) y el riesgo de bus factor si esa transferencia no ocurre.

**Fórmula de referencia para el costo real de un ítem:** costo de la persona (interna o freelance) × tiempo real invertido, **más** el costo de interrupción acumulado si aplicó Expedite (ya definido como mecánica propia), **más** el costo de transferencia de conocimiento si quien lo ejecutó era freelance. Comparar freelance vs. interno solo por tarifa, sin este tercer término, subestima sistemáticamente el costo del freelance.

### 12.3 Categorías mínimas de presupuesto operativo a trackear

- Personal interno (costo cargado).
- Personal freelance/contratistas, con fecha de fin de contrato visible (regla ya definida en 6.1).
- Herramientas y licencias (tablero, CI/CD, monitoreo).
- Infraestructura de ambientes (test/staging/producción).
- Costo de incidentes y soporte, expresado en horas (9.3) y también en su equivalente monetario.
- Reserva declarada para deuda técnica (cuota semanal, 9.4).

### 12.4 Cómo el presupuesto se conecta con la capacidad de portafolio

El piso de capacidad por iniciativa (pilar 3) y el límite de WIP por persona (pilar 2) son, en la práctica, la forma en que el presupuesto se traduce en asignación real de personas. Una iniciativa nueva no se financia con "dinero adicional" que no tiene dónde aterrizar: se financia con capacidad que hoy está en otra iniciativa de menor WSJF, o con dotación nueva (interna o freelance, según 6.1) que entra a la vista única de capacidad como cualquier otra persona.

**Regla de gobierno:** ninguna iniciativa nueva se aprueba financieramente sin verificar antes, con el Diagnóstico 360 y la vista única de capacidad, que existe piso de capacidad disponible o que se libera capacidad de una iniciativa de menor prioridad.

### 12.5 Indicadores de eficiencia de costo (extensión de la sección 9)

- % de capacidad total real dedicada a mantener el negocio vs. cambiar el negocio, contra lo declarado.
- Costo por unidad de throughput entregada (costo de dotación ponderado sobre el throughput de la sección 9.1).
- Costo de interrupción acumulado (9.3) expresado también en moneda, no solo en horas.
- % de presupuesto de dotación en freelance vs. interno, y su tendencia en el tiempo.

### 12.6 Cadencia

El presupuesto y la dotación se revisan en la misma recalibración trimestral del pilar 7 (hoja de ruta, paso 5), no como un proceso financiero aislado y desconectado del resto del flujo.

## 13. Cómo evoluciona este framework

KPS usa versionado semántico (`MAJOR.MINOR.PATCH`): cambios de `MAJOR` alteran un pilar fundamental, `MINOR` agrega una mecánica o sección nueva sin romper lo anterior, `PATCH` corrige o aclara texto existente. Cada cambio se registra en [`CHANGELOG.md`](./CHANGELOG.md).

Cualquier persona o equipo que use KPS puede proponer cambios siguiendo el proceso descrito en [`CONTRIBUTING.md`](./CONTRIBUTING.md). La idea explícita de este framework es que se ponga a prueba en más de un equipo y mejore con esa evidencia, no que quede congelado en su primera versión.

---

## Anexo: SAFe en profundidad

*Nota: SAFe se actualiza periódicamente (la versión mayor más reciente es SAFe 6.0). Esta sección refleja su estructura general y estable en el tiempo; antes de usarla en un material externo o formal, vale la pena confirmar los detalles vigentes en scaledagileframework.com.*

SAFe (Scaled Agile Framework) es el marco de trabajo más usado para escalar prácticas ágiles en organizaciones grandes, combinando principios de Lean, Agile y pensamiento de sistemas en distintas capas: equipo, programa, solución y portafolio. KPS toma prestada únicamente su capa de portafolio; el resto se describe aquí solo como contexto.

**Las siete competencias básicas de SAFe:**

1. Agilidad de equipo y técnica.
2. Entrega ágil de producto.
3. Entrega de soluciones empresariales.
4. Gestión ágil de portafolio (Lean Portfolio Management) — la competencia de la que KPS toma la mayor parte.
5. Agilidad organizacional.
6. Cultura de aprendizaje continuo.
7. Liderazgo Lean-Agile.

**Las cuatro configuraciones de SAFe:**

- Essential SAFe: un solo Tren de Valor con varios equipos.
- Large Solution SAFe: múltiples Trenes de Valor coordinados en una solución grande.
- Portfolio SAFe: agrega gestión de portafolio para alinear estrategia e inversión — la configuración de la que KPS toma su inspiración principal.
- Full SAFe: la combinación completa para organizaciones muy grandes.

**Los diez principios Lean-Agile de SAFe:**

1. Tener una visión económica de las decisiones.
2. Aplicar pensamiento sistémico.
3. Asumir variabilidad; preservar opciones.
4. Construir de forma incremental con ciclos rápidos de aprendizaje integrado.
5. Basar los hitos en la evaluación objetiva de sistemas funcionando.
6. Visualizar y limitar el trabajo en curso, reducir el tamaño de los lotes y gestionar las colas.
7. Aplicar cadencia y sincronizar con planificación entre dominios.
8. Liberar la motivación intrínseca de los trabajadores del conocimiento.
9. Descentralizar la toma de decisiones.
10. Organizarse alrededor del valor.

**Comparación con otros frameworks de escalado:**

| Framework | Enfoque | Cuándo suele preferirse |
|---|---|---|
| **SAFe** | El más estructurado y prescriptivo; agrega capas de programa y portafolio | Organizaciones grandes que gobiernan inversión y estrategia entre muchos equipos |
| **Nexus** (Scrum.org) | Extensión ligera de Scrum para 3-9 equipos, con equipo de integración para dependencias cruzadas | Escalado moderado, cerca de Scrum estándar |
| **LeSS** (Large Scale Scrum) | Minimalista: un solo Product Backlog y un solo Product Owner para varios equipos | Organizaciones que priorizan simplicidad |
| **Scrum@Scale** (Scrum Inc.) | Arquitectura modular "libre de escala", con red de Scrums de Scrums y capa ejecutiva | Escalado orgánico sin framework monolítico |

KPS no adopta ninguno de los cuatro por completo: toma la lógica de portafolio de SAFe y la combina con Kanban a nivel de equipo, dejando fuera la capa de programa que ni Nexus, ni LeSS, ni Scrum@Scale, ni SAFe completo resolverían mejor para un equipo de este tamaño.

## Anexo: glosario de siglas y términos

**ART (Agile Release Train / Tren de Valor Ágil).** En SAFe, un grupo de 50 a 125 personas organizado alrededor de un mismo flujo de valor. No se adopta en KPS por ser una escala demasiado grande.

**Backlog.** Lista completa de trabajo pendiente, sin priorizar todavía.

**Bus factor (factor de camión).** Cuántas personas tendrían que "desaparecer" del equipo para que un conocimiento crítico se pierda por completo.

**Class of Service / Clase de servicio.** Categoría que define cómo se comporta un tipo de trabajo dentro del flujo, con reglas de prioridad y límite propias.

**Costo de demora (Cost of Delay).** Estimación de cuánto se pierde por cada semana que un ítem no se atiende. Base numérica del WSJF.

**Deuda técnica.** Trabajo pendiente de mejora o corrección pospuesto para entregar algo más rápido.

**Definición de Hecho (Definition of Done).** Lista de condiciones que un ítem debe cumplir antes de considerarse terminado.

**Definición de Listo (Definition of Ready).** Condiciones que un ítem debe cumplir antes de entrar a desarrollo (criterios de aceptación y de prueba definidos).

**Expedite.** La clase de servicio más urgente en Kanban: puede saltar la fila normal, pero debe estar limitada en cantidad.

**Flujo de valor (Value Stream).** Agrupación del trabajo según el valor de negocio que entrega de principio a fin.

**Inspect & Adapt (I&A).** Evento de SAFe de revisión y ajuste del proceso. En KPS se adapta como ritual semanal.

**Kanban.** Método de gestión visual del trabajo basado en flujo continuo y límites de trabajo en curso.

**Lead time.** Tiempo total desde que un ítem entra al sistema hasta que se completa.

**Lean Portfolio Management (LPM).** Capa de SAFe que decide cómo se reparte capacidad y presupuesto entre iniciativas o flujos de valor.

**PI (Program Increment).** Ciclo de planificación de SAFe de 8 a 12 semanas. En KPS se reemplaza por un espacio trimestral corto.

**PI Planning.** Evento de planificación de un Program Increment. En KPS, una sesión de medio día por trimestre.

**Portfolio Kanban.** Tablero de SAFe con el estado de todas las iniciativas del portafolio en una sola vista.

**SAFe (Scaled Agile Framework).** Framework para escalar prácticas ágiles a organizaciones grandes.

**Scrum.** Framework ágil basado en ciclos de duración fija (sprints).

**Shift-left.** Práctica de mover actividades de calidad (definir pruebas, revisar seguridad) más temprano en el proceso, en vez de dejarlas solo al final.

**WIP (Work In Progress / Trabajo en curso).** Cantidad de ítems activos en un momento dado. Limitarlo es el principio central de Kanban.

**WSJF (Weighted Shortest Job First).** Método de priorización de SAFe: costo de demora dividido entre tamaño del trabajo.
