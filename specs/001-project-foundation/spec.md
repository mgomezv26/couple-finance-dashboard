# 001 — Fundación del proyecto

Fecha: 2026-10-15. Alcance: infraestructura documental para desarrollo con agentes.

## Necesidad

Un coding agent debe poder identificar el estado real, las restricciones y el proceso de cambio sin inferir funcionalidades inexistentes ni acceder a proyectos privados.

## Situación inicial comprobada

El árbol de trabajo contenía únicamente README.md y el directorio interno .git. El README describía la intención de usar Python, Streamlit y Google Sheets. No existían código, datos, dependencias, tests ni instrucciones para agentes. No se ha copiado contenido externo.

## Requisitos y aceptación

| ID | Requisito | Criterio verificable |
| --- | --- | --- |
| F01 | Entrada de agentes | AGENTS.md describe la secuencia de lectura, implementación mínima, verificación y límites de commit/push; enlaza todas las capas. |
| F02 | Reglas concretas | Seis reglas separadas con propósito, alcance, aplicación y decisiones, incluyendo privacidad y frontera de datos. |
| F03 | Procedimientos reutilizables | Tres skills válidas de implementación, revisión y comprobación de release, sin autorizar trabajo fuera de alcance. |
| F04 | Principios y proceso | Constitución con siete principios y flujo completo/reducido de specs documentado. |
| F05 | Estado honesto | Cinco documentos de memoria y seis de contexto distinguen estado real, previsto y no decidido. |
| F06 | Decisiones explícitas | Tres ADRs con Status, Context, Decision y Consequences sobre fuentes, Google y privacidad pública. |
| F07 | Cierre verificable | Enlaces locales válidos, revisión de privacidad y redundancias, y evidencia en checklist; README coherente. |

## Preparación de fuentes

Documentar demo sintética y futura fuente Google Sheets, con acceso mediante `services/data_loader.py`. No crear ese módulo ni definir su interfaz o entidades antes de una spec posterior.

## Fuera de alcance

Dashboard completo, páginas financieras, datos de ejemplo ejecutables, integración Google funcional, OAuth, autenticación, despliegue, base de datos, código copiado de proyectos privados, commit y push. No se deciden indicadores, tablas o pantallas futuras.

## Incertidumbres diferidas

Modelo de datos, formato demo, versiones, dependencias, pruebas de app y configuración Google se resolverán en sus specs de implementación. No bloquean esta entrega documental porque no se afirma que exista una aplicación.
