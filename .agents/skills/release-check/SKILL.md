---
name: release-check
description: Evaluar una futura entrega ejecutable del proyecto revisando demo, privacidad, tests y reproducibilidad, sin publicar.
---

# Comprobación de entrega

Carga [AGENTS.md](../../../AGENTS.md), la spec de la entrega y [development.md](../../../docs/context/development.md). Comprueba con archivos y ejecuciones reales:

| Punto | Evidencia |
| --- | --- |
| Demo funcionando | Arranque y recorrido básico con datos ficticios, sin conexión ni credenciales Google. |
| Secrets ausentes | Revisión del contenido a entregar y del diff conforme a [privacy.md](../../rules/privacy.md). |
| Tests correctos | Comandos aplicables y resultados sin fallos pendientes. |
| README coherente | Instrucciones y capacidades que coincidan con la entrega. |
| Requirements correctos | Dependencias declaradas concordantes con imports e instalación limpia. |
| Datos ficticios | Procedencia sintética confirmada de ejemplos y fixtures. |
| Configuración reproducible | Preparación desde un checkout limpio con instrucciones publicadas. |

Clasifica cada punto como aprobado, fallido o no comprobable, con evidencia. La ausencia de app, dependencias o tests en esta fase impide aprobar una entrega ejecutable: no los crees para superar la revisión. El cierre documental usa su [checklist propio](../../../specs/001-project-foundation/checklists/foundation.md).

Devuelve el estado de preparación y los impedimentos. No publiques, despliegues ni hagas commit o push.
