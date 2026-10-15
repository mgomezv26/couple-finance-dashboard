# Plan de fundación

## Diseño de la entrega

Crear documentos Markdown originales a partir de la petición y de la inspección local. Conservar la identidad del README y añadir estado real y enlaces. No añadir código, dependencias o configuración de servicios.

| Capa | Responsabilidad exclusiva |
| --- | --- |
| AGENTS.md | Orientación y secuencia de trabajo. |
| .agents/rules | Restricciones operativas por responsabilidad. |
| .agents/skills | Procedimientos repetibles por tipo de tarea. |
| .specify/memory/constitution.md | Principios duraderos y gobierno. |
| specs/001-project-foundation | Requisitos, diseño, ejecución y evidencia de esta entrega. |
| docs/context | Hechos estables y límites del diseño previsto. |
| docs/adr | Motivación y consecuencias de decisiones. |
| memory-bank | Resumen breve del estado actual. |

## Contraste constitucional

Privacidad: solo texto original sin datos reales. Independencia y demo: documentar requisitos futuros sin afirmar implementación. Spec previa: delimitar esta entrega. Simplicidad: sin código auxiliar permanente ni dependencias. Mantenibilidad: enlaces al detalle en lugar de copias. Verificación: revisión de inventario, enlaces, skills, contenido y diff.

## Ejecución y convergencia

Seguir [tasks.md](tasks.md). Validar enlaces relativos y frontmatter de skills; revisar todos los archivos, incluidos nuevos no versionados. Buscar patrones sensibles sin reproducir posibles valores. Revisar manualmente redundancias y la distinción entre estado actual y futuro. Registrar resultados en [checklists/foundation.md](checklists/foundation.md) y cerrar la memoria solo tras superar las comprobaciones.

## Riesgos concretos

- La repetición del mismo hecho entre capas puede divergir: usar resúmenes con enlace a una fuente de detalle.
- Un diagrama previsto puede parecer código existente: etiquetar explícitamente el estado.
- El diff no incluye archivos nuevos sin staging: recorrer también el inventario completo.
- Un escaneo de patrones puede omitir datos personales: complementarlo con lectura manual y revisión de procedencia.
