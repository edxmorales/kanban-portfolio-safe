# Propuesta de piloto 1 (anonimizada) — de un diagnóstico real al primer backlog KPS

> Continúa el [Caso de aplicación 1](./caso-aplicacion-01-diagnostico-seguridad.md). Mismo criterio de anonimización: sin nombres de personas, empresas, productos ni identificadores de infraestructura.

## Punto de partida

El equipo ya completó el frente 4 (Ciberseguridad) del Diagnóstico 360° de TI de alcance amplio (sección 0.1) sobre su plataforma productiva, además de avances en varios de los otros frentes. Tiene, por tanto, algo que la mayoría de los pilotos de KPS no tiene al empezar: **una línea base real, con números, en vez de una fecha de inicio arbitraria.** Esto es exactamente el estado en el que la sección 9.9 de `FRAMEWORK.md` (indicadores para validar el piloto) espera encontrar a un equipo antes de arrancar — y es también el momento correcto para completar, ahora sí, los cinco ángulos propios del Diagnóstico 360 de KPS (sección 0) antes del Paso 1 de la hoja de ruta.

Los hallazgos ya identificados por el equipo (independientemente de KPS, antes de conocer el framework) llegaron organizados como una lista de prioridades. Esa lista es, sin que nadie lo hubiera planeado así, casi un backlog de KPS a la espera de clasificarse.

## Paso 1: clasificar los hallazgos existentes en clases de servicio

| Hallazgo (generalizado) | Clase de servicio KPS | Justificación |
|---|---|---|
| Un despliegue sin todas sus réplicas disponibles | **Expedite acotado** (no es incidente activo, pero es inestabilidad latente en producción) | No afecta al usuario final hoy, pero es el tipo de hallazgo que la guardia rotativa (sección 4) debería tomar en su semana de turno, no dejar para "cuando haya tiempo". |
| Definir autoescalamiento (HPA) y ajustar el techo de capacidad con límites de costo | **Fecha fija** dentro del flujo de valor de plataforma/infraestructura | Tiene alcance definido y una fecha razonable de entrega — no es urgente hoy, pero tiene una ventana antes de que la capacidad vuelva a tocar el techo. |
| Activar cifrado obligatorio en tránsito tras pruebas de compatibilidad | **Estándar, priorizado alto vía WSJF** | Costo de demora alto (expone tráfico interno sin cifrar) frente a un tamaño de trabajo pequeño (activar una bandera ya soportada) — WSJF alto casi por definición. |
| Pasar reglas de seguridad de modo registro a modo bloqueo, empezando por la de mayor riesgo | **Estándar, con revisión de falsos positivos antes de cada activación** | Requiere validación previa (ventana de observación, sección 8) antes de convertirse en bloqueo activo — no se activa todo de una vez. |
| Estandarizar las automatizaciones como infraestructura como código con ticket, evidencia y rollback documentado | **Deuda técnica (Intangible)**, con cuota semanal declarada | Es exactamente la mecánica de "interés creciente sobre deuda técnica" (sección 4): cada semana sin estandarizar, el costo de mantenerlo manual sube. |
| Construir un tablero semanal antes/después (conexiones, errores, pods, réplicas, WAF, capacidad) | No es un ítem de backlog — **es el sistema de medición de la sección 9 de KPS, ya especificado** | El equipo llegó, por su cuenta, a pedir exactamente lo que la sección 9 ya resuelve. No hace falta diseñarlo desde cero: se adopta directamente. |

## Paso 2: flujo de valor propuesto para el piloto

Se recomienda declarar **"Plataforma e Infraestructura"** como un flujo de valor propio (pilar 5), separado de los flujos de valor de producto — precisamente porque hoy varios productos comparten esta misma capacidad de infraestructura sin una vista conjunta, que es el patrón exacto que el pilar 1 (una sola vista de capacidad) busca corregir.

## Paso 3: roles a nombrar antes de empezar

Dado que varios de los hallazgos tienen impacto de seguridad con consecuencia de negocio (exposición de datos, disponibilidad del servicio), este piloto es un buen primer caso para nombrar, desde el día uno:

- **Aprobador de Clase de Servicio**, con criterio explícito y por escrito de qué hallazgo de seguridad amerita Expedite y cuál puede esperar al ritual semanal — evita que "es de seguridad" se use como comodín para saltarse la fila siempre.
- **Representante de Valor de Negocio** del flujo de Plataforma e Infraestructura — quien estime el costo de demora real de un hallazgo de seguridad no es un ejercicio técnico solamente, así que este rol necesita a alguien con visibilidad del impacto de negocio de una brecha o una caída de disponibilidad.
- **Respaldo nombrado** para ambos roles desde el inicio (sección 5), dado que la naturaleza de estos hallazgos no puede esperar a que alguien vuelva de vacaciones.

## Paso 4: duración y criterio de éxito

Siguiendo el paso 8 de la hoja de ruta (sección 11): piloto acotado de 4 a 6 semanas, en este único flujo de valor de Plataforma e Infraestructura, con el criterio de decisión de la sección 9.9 acordado **antes** de empezar:

- Línea base "antes" = los números que este mismo diagnóstico ya capturó (capacidad de nodos, salud de pods y despliegues, cantidad de reglas de seguridad aún en modo registro, ítems de deuda técnica de infraestructura pendientes).
- Métrica compuesta a revisar cada semana (sección 9.7): eficiencia de flujo, cumplimiento de WIP, índice de concentración, y en este caso específico, se recomienda añadir un quinto indicador de seguimiento propio del piloto: **% de reglas de seguridad en modo bloqueo activo sobre el total identificado como candidato**, dado que es el hallazgo con mayor costo de demora de este caso.
- Al cerrar el piloto, aplicar el mismo criterio go/no-go ya definido: expandir si al menos tres de los cuatro (o cinco, con el indicador propio de este piloto) indicadores mejoran de forma sostenida.

## Por qué este caso es una buena evidencia para KPS, no solo para esta organización

Lo más útil de este caso no es la lista de hallazgos en sí — es que **el equipo llegó de forma independiente, sin haber leído KPS todavía, a pedir casi exactamente las mismas piezas que el framework ya prescribe**: una vista consolidada de riesgos, una forma de priorizar objetivamente, una cuota para la deuda técnica que compite contra lo urgente, y un tablero de medición antes/después. Eso no valida que KPS sea perfecto, pero sí es una señal fuerte de que las piezas del framework responden a necesidades reales y recurrentes, no a preferencias de diseño de quien lo escribió.
