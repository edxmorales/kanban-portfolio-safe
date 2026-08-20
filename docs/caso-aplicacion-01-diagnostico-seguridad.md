# Caso de aplicación real (anonimizado) — Frente 4 (Ciberseguridad) del Diagnóstico 360° de TI

> Este documento describe una aplicación real de la relación entre el [Diagnóstico 360 de KPS](../FRAMEWORK.md#0-diagnóstico-360-el-punto-de-partida-obligatorio) y el [Diagnóstico 360° de transformación de TI de alcance más amplio](../FRAMEWORK.md#01-relación-con-el-diagnóstico-360-de-transformación-de-ti-alcance-más-amplio) (sección 0.1), con todos los datos que podrían identificar a la organización, sus productos o a las personas involucradas eliminados o generalizados. Los números operativos (cantidad de nodos, pods, funciones, etc.) se conservan porque no identifican a nadie y son justamente lo que hace este caso útil para otros equipos.

## Contexto

Un equipo de infraestructura ejecutó el **frente 4 (Ciberseguridad)** del Diagnóstico 360° de TI de alcance amplio descrito en la sección 0.1 — vulnerabilidades, accesos, respaldos, continuidad y madurez de seguridad de una plataforma productiva en la nube (Kubernetes + funciones serverless + base de datos gestionada), compartida por varios productos de un mismo portafolio. Este frente se abordó junto con los frentes 1 al 4 (ya estabilizados) y en paralelo a avances parciales en los frentes 6, 8, 9 y 10, mientras los frentes 5 y 7 quedaban para una siguiente etapa.

La sección 0.1 de `FRAMEWORK.md` es explícita en que el diagnóstico del frente 4 en sí queda fuera de alcance del Diagnóstico 360 de **KPS** (los cinco ángulos de la sección 0, enfocados en flujo de trabajo y portafolio, no en infraestructura) — KPS no audita vulnerabilidades ni controles de seguridad. Este caso es justamente un ejemplo de por qué esa distinción importa en la práctica: el equipo necesitó completar este frente de seguridad, con su propia disciplina, **antes** de que KPS entrara a operar la capa de flujo de trabajo — y lo que ese frente reveló terminó alimentando directamente el primer backlog del piloto KPS (ver [Propuesta de piloto 1](./propuesta-piloto-01.md)), tal como describe la tabla de la sección 0.1.

**Nota metodológica:** este es el primer caso de aplicación real documentado para KPS — ver [CONTRIBUTING.md](../CONTRIBUTING.md) sobre cómo el framework evoluciona con evidencia de uso real.

## Qué reveló el diagnóstico

| Componente revisado | Hallazgo | Lectura bajo el lente de KPS |
|---|---|---|
| Conexiones a base de datos | Procesos automáticos abrían conexiones directas y repetitivas a la base de datos, sin una capa intermedia que las controlara. | Riesgo invisible hasta que satura — el mismo tipo de patrón que el ángulo 4 de KPS (PRs y flujo de código) busca exponer del lado del código, aplicado aquí del lado de la infraestructura. |
| Escalamiento de capacidad | El grupo de nodos productivos ya estaba en su capacidad máxima configurada (mínimo, deseado y máximo coincidían). No existía autoescalamiento de aplicación (HPA) por CPU, memoria o métrica de negocio. | Un techo de capacidad alcanzado sin mecanismo de reacción automática es un piso de capacidad implícito no declarado — lo que el pilar 3 de KPS (piso de capacidad por iniciativa) busca hacer explícito, aplicado aquí a infraestructura y no solo a personas. |
| Controles de seguridad perimetral (WAF) | Varias reglas de seguridad avanzadas estaban configuradas solo en modo de registro (Count), sin bloquear tráfico real, para varios productos del portafolio. | Una protección que "existe en el papel" pero no actúa es deuda técnica de seguridad — candidata directa a la mecánica de interés creciente sobre deuda técnica (sección 4) si no se prioriza. |
| Cifrado en tránsito | El cifrado obligatorio de conexiones a la capa intermedia de base de datos estaba desactivado en el total de las instancias revisadas, pendiente de pruebas de compatibilidad. | Un control de seguridad pendiente de activar, no de construir — clasifica naturalmente como Estándar de alta prioridad vía WSJF (sección 3, pilar 3), no como proyecto nuevo. |
| Salud de despliegues | De un número alto de despliegues activos, todos menos uno tenían sus réplicas completamente disponibles. | El mismo principio del ángulo 3 de KPS (estado real de cada iniciativa) aplicado a infraestructura: un solo despliegue rezagado es fácil de perder de vista sin una vista consolidada. |
| Automatización y reversión | Las funciones automatizadas revisadas ya usaban versiones publicadas con un paquete anterior disponible como ruta de reversión antes de cada cambio. | Esto es exactamente la práctica que la sección 8 de KPS (plan de rollback definido antes de desplegar) recomienda — el equipo ya la aplicaba de forma independiente, antes de conocer el framework. |
| Gestión de credenciales | Las credenciales de acceso a servicios se gestionaban de forma centralizada (gestor de secretos), no incrustadas en configuración manual. | Buena práctica ya presente — el diagnóstico también sirve para confirmar qué **no** hace falta cambiar, no solo para encontrar huecos. |

## La lección general (más allá de este caso)

Ningún hallazgo de este diagnóstico fue una sorpresa dramática — y esa es precisamente la lección. La mayoría de los riesgos de seguridad e infraestructura no son incidentes que aparecen de la nada: son controles que **ya se decidieron pero no se activaron completamente** (reglas en modo de registro en vez de bloqueo, cifrado pendiente de un último paso, un techo de capacidad ya tocado sin que nadie lo declarara formalmente). El Diagnóstico 360 no los descubre porque sea especialmente perceptivo — los descubre porque **es el primer momento en que alguien los mira todos juntos, con números, en vez de por separado y de memoria.**

Esto confirma, con evidencia real, algo que KPS ya asumía en su diseño: el problema rara vez es la falta de buenas prácticas individuales — casi siempre existen, dispersas. El problema es la falta de una vista única que las junte y les ponga una prioridad explícita frente a todo lo demás que compite por la misma capacidad.

## Qué sigue

Este caso continúa en la [Propuesta de piloto 1](./propuesta-piloto-01.md), donde los hallazgos de esta tabla se clasifican en clases de servicio de KPS y se organizan como el primer backlog de un piloto real.
