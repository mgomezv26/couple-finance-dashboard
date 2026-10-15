---
name: code-review
description: Revisar cambios de este repositorio frente a su spec, arquitectura, privacidad y verificaciones, con hallazgos accionables.
---

# Revisión

Lee [AGENTS.md](../../../AGENTS.md), la spec afectada, el diff completo y los consumidores reales. Si no existe código, limita la revisión a documentación e indica ese alcance.

- **Correctness:** comportamiento y casos límite frente a requisitos comprobables.
- **Spec compliance:** criterios cubiertos y cambios fuera de alcance.
- **Privacidad:** aplica [privacy.md](../../rules/privacy.md) sin reproducir posibles secretos.
- **Duplicación:** lógica o documentación que pueda divergir.
- **Arquitectura:** separación UI/datos y acceso a través del cargador previsto.
- **Manejo de errores:** fallos visibles y sin filtrar configuración privada.
- **Tests:** cobertura de lógica relevante, evidencia de ejecución y fallos pendientes.
- **Documentación:** coherencia entre implementación, contexto, ADRs y memoria.

Informa primero de defectos verificables, por impacto, con archivo, ubicación, consecuencia y corrección sugerida. Separa preguntas de fallos demostrados. Si no hay hallazgos, dilo e indica las comprobaciones no realizadas. La revisión por sí sola no autoriza cambios de código, commit ni push.
