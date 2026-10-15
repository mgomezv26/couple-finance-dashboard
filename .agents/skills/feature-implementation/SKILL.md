---
name: feature-implementation
description: Implementar un cambio de este repositorio a partir de una spec, con verificación, privacidad y actualización del contexto.
---

# Implementación de un cambio

1. Carga [AGENTS.md](../../../AGENTS.md), el contexto relevante y [activeContext.md](../../../memory-bank/activeContext.md).
2. Localiza la spec en [specs](../../../specs/). Si no cubre el cambio, define requisitos siguiendo [development.md](../../../docs/context/development.md).
3. Inspecciona código real y cambios locales; conserva el trabajo previo del usuario.
4. Contrasta requisitos, criterios de aceptación, exclusiones y reglas aplicables. Resuelve ambigüedades materiales antes de implementar lo dependiente.
5. Implementa el cambio mínimo autorizado. La spec de fundación no autoriza construir la app.
6. Ejecuta tests relevantes. Si no hay código, aplica las comprobaciones documentales de [testing.md](../../../docs/context/testing.md). Corrige fallos antes de cerrar tareas.
7. Revisa contenido nuevo y diff conforme a [privacy.md](../../rules/privacy.md), incluyendo fixtures y mensajes de error.
8. Actualiza contexto estable y ADRs cuando cambien hechos o decisiones; registra evidencias en el checklist de la spec.
9. Actualiza memory-bank si cambia el foco o el estado del proyecto.

Entrega cambios, verificaciones y limitaciones. No hagas commit, push ni avances a otra fase sin petición explícita.
