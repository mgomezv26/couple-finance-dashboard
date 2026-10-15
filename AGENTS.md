# Entrada para coding agents

Este repositorio está en fase de fundación documental. No presupongas que existen una app, un cargador de datos o tests: comprueba el árbol y el código real.

## Secuencia de trabajo

1. Lee este `AGENTS.md`.
2. Carga únicamente la documentación relevante de [docs/context](docs/context/).
3. Lee [memory-bank/activeContext.md](memory-bank/activeContext.md).
4. Busca una spec relacionada en [specs](specs/). Antes de implementar comportamiento nuevo, define sus requisitos; no extrapoles funcionalidades de la spec de fundación.
5. Inspecciona el código real y los cambios locales antes de asumir comportamiento o editar.
6. Aplica las reglas relevantes de [.agents/rules](.agents/rules/); privacidad y documentación afectan también a cambios sin código.
7. Implementa el cambio mínimo que satisface el alcance autorizado.
8. Ejecuta las verificaciones aplicables y registra resultados y limitaciones. Una comprobación fallida impide declarar completa la tarea afectada.
9. Actualiza contexto estable, ADRs o memory-bank cuando corresponda, evitando copiar el mismo contenido entre capas.
10. No hagas commit ni push salvo petición explícita del usuario.

## Mapa de contexto

| Capa | Función y entrada |
| --- | --- |
| Principios | [.specify/memory/constitution.md](.specify/memory/constitution.md): restricciones duraderas. |
| Contexto | [docs/context](docs/context/): producto, arquitectura, flujo, modelo, pruebas y desarrollo. |
| Specs | [specs](specs/): qué, cómo, tareas y verificación de cada cambio. El flujo se define en [development.md](docs/context/development.md). |
| Rules | [.agents/rules](.agents/rules/): privacidad, Python, Streamlit, acceso a datos, testing y documentación. |
| Skills | [.agents/skills](.agents/skills/): procedimientos reutilizables; cargar solo el apropiado. |
| Memory | [memory-bank](memory-bank/): estado actual resumido, no historial exhaustivo. |
| ADRs | [docs/adr](docs/adr/): motivos y consecuencias de decisiones arquitectónicas. |

## Selección de skills

- [feature-implementation](.agents/skills/feature-implementation/SKILL.md): implementar un cambio con una spec definida.
- [code-review](.agents/skills/code-review/SKILL.md): revisar cambios y comunicar hallazgos.
- [release-check](.agents/skills/release-check/SKILL.md): evaluar preparación para una entrega ejecutable; no autoriza publicación.

El alcance de esta fundación está en [001-project-foundation](specs/001-project-foundation/spec.md). Los contratos futuros de arquitectura se documentan como previstos, no como código existente.
