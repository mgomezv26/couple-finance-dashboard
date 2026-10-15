# 002 — Fuente de datos demo

Fecha: 2026-10-15. Estado: CLARIFY cerrado; preparada para PLAN. Feature no implementada ni completada.

## Objetivo

Permitir que una persona clone el repositorio público, instale las dependencias y ejecute una primera versión funcional con datos ficticios incluidos en el proyecto, sin Google Sheets, credenciales, `secrets.toml`, cuentas externas ni datos personales reales.

Esta especificación define QUÉ necesita la demo y el contrato conceptual de datos que consumirán las futuras páginas, independientemente de su origen. No define un formato de almacenamiento, una base de datos ni una interfaz de funciones Python.

## Situación inicial y referencias

La inspección local muestra únicamente documentación: no existen aplicación, cargador, datasets, dependencias declaradas ni tests de aplicación. La [fundación](../001-project-foundation/spec.md) está completada. El [roadmap](../../docs/ROADMAP.md) sitúa esta feature antes de Google Sheets y de los dashboards.

Se mantienen la [constitución](../../.specify/memory/constitution.md), la [arquitectura prevista](../../docs/context/architecture.md), el [flujo](../../docs/context/data-flow.md) y la [regla de acceso a datos](../../.agents/rules/data-access.md). Esta spec es la fuente de verdad de los requisitos de 002; el [modelo de contexto](../../docs/context/data-model.md) resume los hechos estables acordados, sin afirmar que estén implementados.

## Alcance

- Inicio y uso básico identificable como demo, sin configuración privada.
- Datos sintéticos de Alex y Sam para movimientos, cuentas, saldos y un objetivo de compra de vivienda.
- Información de seis meses, con los cuatro tipos de movimiento y las tres clases de cuenta solicitadas; no se exige el mismo número de movimientos por mes.
- Contrato común de lectura con significado, tipos conceptuales y consistencia independientes del origen.
- Evidencia futura de arranque reproducible y validez del conjunto demo.

El cierre de CLARIFY actualiza este `spec.md` y las partes necesarias de `docs/context/data-model.md`. Los requisitos siguientes describen el resultado futuro de la feature, no trabajo ejecutado ahora.

## Fuera de alcance

Fuera de la feature 002: Google Sheets funcional (fase 003), OAuth, cuentas de servicio reales, edición de movimientos/cuentas/saldos/objetivos, gestión editable de categorías, múltiples monedas, autenticación, base de datos, dashboard financiero completo, property tracker, hipotecas, simulador de compra, despliegue y múltiples objetivos avanzados. Las fases posteriores siguen definidas únicamente en el roadmap.

Fuera de esta tarea documental: implementar el cargador o la app, elegir funciones, librerías, caché o formatos de almacenamiento y crear `plan.md` o `tasks.md`. El cargador sí forma parte del resultado futuro de 002; su diseño técnico corresponde a PLAN.

## Actores y user stories

| ID | Actor y necesidad | Resultado esperado |
| --- | --- | --- |
| US01 | Persona que explora el repositorio público | Iniciar una demo funcional sin disponer de Google ni configuración privada. |
| US02 | Persona que consulta la demo | Reconocer que los datos son ficticios y corresponden a Alex y Sam. |
| US03 | Persona que desarrolla futuras páginas | Consumir las cuatro entidades con significado estable sin conocer el origen de los datos. |

Alex y Sam son sujetos ficticios de los datos, no cuentas de autenticación.

## Requisitos funcionales

| ID | Requisito |
| --- | --- |
| RF01 | Desde un checkout limpio, las instrucciones de instalación y ejecución deben permitir iniciar la app demo sin configuración privada ni cuentas externas. |
| RF02 | La ejecución demo no debe necesitar Google, sus credenciales o su disponibilidad; la ausencia de `secrets.toml` no debe impedir el arranque. |
| RF03 | El usuario debe ver la indicación «Modo DEMO» y reconocer el carácter ficticio de los datos durante su uso. |
| RF04 | Los datos incluidos deben proporcionar movimientos, cuentas, saldos y objetivos conforme al contrato de esta spec. La demo utiliza EUR, muestra € y expresa cantidades con precisión de dos decimales. |
| RF05 | Los movimientos deben cubrir seis meses e incluir Ingreso, Gasto, Devolución y Transferencia, con representación de Alex y Sam. No se exige igual número de movimientos por mes. |
| RF06 | Cada persona debe disponer, como mínimo, de una cuenta corriente, una de ahorro y una de efectivo: al menos seis cuentas distinguibles en total. |
| RF07 | Debe existir un único objetivo conjunto ficticio «Compra vivienda», con meta, capital inicial propio, capital actual propio, ayuda familiar separada y estado activo. El capital propio destinado a vivienda procede conceptualmente solo de cuentas activas marcadas como participantes. |
| RF08 | Todas las referencias a personas y cuentas deben ser válidas; los saldos, movimientos y objetivos deben ser coherentes según las reglas de negocio aclaradas. |
| RF09 | La futura capa común debe proporcionar las cuatro entidades sin obligar a sus consumidores a interpretar CSV, columnas de Sheets o detalles de una fuente. Se respeta la frontera ya acordada en `services/data_loader.py`, sin diseñar su implementación. |
| RF10 | Si falta un dataset requerido, un campo obligatorio, hay una referencia inválida o no se cumple el contrato mínimo, debe mostrarse un error comprensible al usuario/desarrollador. No continuar silenciosamente como si la demo fuera válida ni consultar Google como alternativa. La técnica de validación pertenece a PLAN. |
| RF11 | El recorrido mínimo debe permitir comprobar el arranque correcto y la carga de movimientos, cuentas, saldos y objetivos, sin construir los dashboards finales. |
| RF12 | El modo demo es de solo lectura; no permite editar ninguna de las cuatro entidades. |

## Requisitos de privacidad

- RP01: crear todos los datos desde cero para esta demo; no copiar, transformar ni anonimizar datos del proyecto privado.
- RP02: utilizar únicamente Alex y Sam como personas de ejemplo; cuentas, conceptos, notas y cantidades serán sintéticos.
- RP03: no incluir credenciales, identificadores reales, emails reales, rutas personales ni configuración privada en datos, documentación, capturas o errores.
- RP04: revisar la procedencia del conjunto además de buscar patrones sensibles; un escaneo por sí solo no acredita que un importe sea ficticio.

Referencia normativa: [privacy.md](../../.agents/rules/privacy.md).

## Contrato conceptual de datos

### Convenciones comunes

Los nombres siguientes son etiquetas semánticas, no nombres obligatorios de columnas o atributos. «Obligatorio» significa presente y con valor válido; un texto obligatorio no puede estar vacío. «Opcional» permite ausencia, que no equivale a cero ni a falso salvo regla explícita.

- **Persona:** referencia conceptual a una persona. En esta demo el conjunto cerrado es Alex y Sam; el contrato reutilizable no exige esos nombres en futuras fuentes ni nombres hardcodeados en páginas.
- **Cuenta:** referencia resoluble a una cuenta del catálogo y a su titular. Persona + Cuenta permite distinguir cuentas homónimas; una referencia de destino no debe asumir que su titular coincide con Persona del movimiento.
- **Fecha:** fecha de calendario válida, sin hora en 002. Mayor precisión temporal requeriría ampliar el contrato en una feature futura.
- **Dinero:** cantidad decimal finita en EUR, con precisión monetaria de dos decimales y símbolo mostrado €. No se admiten múltiples monedas en 002; no se prescribe representación técnica ni algoritmo de redondeo.
- **Booleano:** verdadero o falso, sin equivalencia implícita con textos de una fuente externa.

No se decide serialización, orden de registros, clases Python, identificadores técnicos ni mecanismo de validación. Las decisiones de producto resueltas no deben reabrirse en PLAN sin nueva justificación. Cuando un campo opcional o no aplicable esté ausente, el contrato admite vacío/null sin convertirlo en cero ni inventar un valor.

### Movimientos

| Campo | Presencia | Tipo conceptual | Significado y valores |
| --- | --- | --- | --- |
| Persona | Obligatorio | Referencia a persona | Alex o Sam; propietaria de Cuenta destino en Ingreso/Devolución y de Cuenta origen en Gasto/Transferencia. |
| Fecha | Obligatorio | Fecha | Día del movimiento. |
| Tipo | Obligatorio | Enumeración | Ingreso, Gasto, Devolución o Transferencia. |
| Importe | Obligatorio | Dinero estrictamente positivo | El signo financiero lo determina Tipo; no almacenar gastos negativos ni movimientos con importe cero. |
| Cuenta origen | Condicional | Referencia a cuenta | Obligatoria en Gasto y Transferencia; vacía/no aplicable en Ingreso y Devolución. |
| Cuenta destino | Condicional | Referencia a cuenta | Obligatoria en Ingreso, Devolución y Transferencia; vacía/no aplicable en Gasto. |
| Categoría | Condicional | Clasificación controlada | Obligatoria en Ingreso, Gasto y Devolución; opcional en Transferencia. Si aparece, pertenece al catálogo demo descrito debajo. |
| Ámbito | Condicional | Enumeración: Personal, Común | Obligatorio en Gasto y Devolución; opcional en Ingreso y Transferencia. Si aparece, solo admite los dos valores indicados. |
| Concepto | Obligatorio | Texto | Descripción breve y ficticia que permita entender el movimiento. |
| Notas | Opcional | Texto | Aclaración ficticia adicional; su ausencia no invalida el movimiento. |

Consistencia: Persona y las cuentas informadas deben existir y cumplir la siguiente matriz. Una transferencia se representa con un único movimiento, sin segundo movimiento espejo; puede realizarse entre cuentas de la misma persona o entre Alex y Sam. No computa como ingreso ni gasto y no modifica el patrimonio conjunto. No deducir duplicados solo por coincidencia de fecha, importe y concepto. Categoría y Ámbito de una Devolución deben permitir identificar el tipo de gasto compensado; no se exige vincularla a un gasto individual.

| Tipo | Cuenta origen | Cuenta destino | Persona propietaria de | Categoría | Ámbito |
| --- | --- | --- | --- | --- | --- |
| Ingreso | Vacía/no aplicable | Obligatoria | Destino | Obligatoria | Opcional |
| Gasto | Obligatoria | Vacía/no aplicable | Origen | Obligatoria | Obligatorio |
| Devolución | Vacía/no aplicable | Obligatoria | Destino | Obligatoria | Obligatorio |
| Transferencia | Obligatoria | Obligatoria, distinta del origen | Origen; destino puede tener otra persona titular | Opcional | Opcional |

El catálogo controlado demo debe incluir ejemplos de Vivienda, Supermercado, Restaurantes / delivery, Transporte, Salud, Compras, Ocio, Viajes, Formación, Suscripciones, Nómina, Ingresos extra y Otros. «Otros» representa casos no previstos. Se admite además «Transferencia entre cuentas» para Transferencia, sin exigir esa categoría ni un ejemplo que la use. No se autoriza gestión editable ni textos arbitrarios fuera del catálogo declarado.

### Saldos

| Campo | Presencia | Tipo conceptual | Significado y valores |
| --- | --- | --- | --- |
| Fecha | Obligatorio | Fecha | Fecha a la que corresponde la observación del saldo. |
| Persona | Obligatorio | Referencia a persona | Titular de la cuenta; Alex o Sam en demo. |
| Cuenta | Obligatorio | Referencia a cuenta | Cuenta cuyo saldo se observa. |
| Saldo | Obligatorio | Dinero | Snapshot explícito; puede ser positivo, cero o negativo, sin restricciones diferentes por tipo de cuenta en 002. |
| Notas | Opcional | Texto | Explicación ficticia de la observación. |

Consistencia: la cuenta debe existir y pertenecer a la Persona. Cada snapshot se identifica conceptualmente por Persona + Cuenta + Fecha; esa combinación debe ser única. Una cuenta puede tener múltiples snapshots en fechas distintas, nunca dos para el mismo día en 002. La fecha permite identificar el más reciente, sin hora ni supuesto de cierre diario. Un saldo ausente no se interpreta como cero. No se exige reconstruir todos los saldos históricos desde movimientos ni sumar snapshots de diferentes fechas como capital adicional. La lógica futura podrá aplicar movimientos posteriores cuando proceda; ese algoritmo no se define aquí. Para vivienda rige la referencia explícita descrita en Objetivos.

### Cuentas

| Campo | Presencia | Tipo conceptual | Significado y valores |
| --- | --- | --- | --- |
| Persona | Obligatorio | Referencia a persona | Titular; Alex o Sam en demo. |
| Cuenta | Obligatorio | Texto identificador conceptual | Nombre ficticio distinguible dentro de las cuentas de esa persona. No es un número bancario. |
| Tipo | Obligatorio | Enumeración para demo | Cuenta corriente, Ahorro o Efectivo. No se decide aquí el catálogo de futuras fuentes. |
| Activa | Obligatorio | Booleano | Indica si la cuenta está activa; no es su saldo ni un permiso de acceso. |
| Participa en objetivo vivienda | Opcional | Booleano | Solo una cuenta activa y explícitamente marcada como participante contribuye al capital propio de vivienda. Ausencia no es una marca afirmativa y no autoriza su inclusión automática. |

Consistencia: no hay cuentas repetidas para la misma combinación Persona + Cuenta. Dos personas pueden usar el mismo nombre de cuenta sin que sus saldos se mezclen. Una cuenta inactiva puede conservar registros históricos; no debe eliminarse de las referencias por estar inactiva. Cuentas compartidas y cambios de titularidad no se presuponen para la demo.

### Objetivos

| Campo | Presencia | Tipo conceptual | Significado y valores |
| --- | --- | --- | --- |
| Nombre del objetivo | Obligatorio | Texto | «Compra vivienda», único objetivo conjunto ficticio de 002. |
| Meta económica | Obligatorio | Dinero | Cantidad objetivo ficticia para la compra de vivienda. |
| Capital inicial propio | Obligatorio | Dinero | Capital propio de partida del objetivo, separado de ayuda pendiente. Su valor y contexto de partida serán explícitos en los datos demo; no se exige reconstruirlo desde el historial de movimientos. |
| Capital actual propio | Obligatorio | Dinero | Capital coherente con el derivado de las cuentas activas participantes para la fecha de referencia utilizada por los datos demo, conforme a la regla siguiente. |
| Ayuda familiar | Obligatorio | Dinero | Dinero externo previsto todavía no incluido en los saldos; no es ahorro propio. Cero representa ausencia de ayuda pendiente. Una cantidad ya depositada no puede volver a contarse aquí. |
| Activo | Obligatorio | Booleano | Indica si el objetivo está activo. |

No se requieren campos opcionales adicionales para objetivos. El objetivo es conjunto y coherente con Alex y Sam. No se impone que el capital actual supere al inicial ni que sea inferior a la meta. Se retira la propuesta previa de restringir todos los capitales a valores no negativos: no fue aprobada y los saldos participantes pueden ser negativos.

**Regla de consistencia del capital:** los datos demo deben identificar la fecha de referencia utilizada. Para esa fecha, cada cuenta activa y marcada como participante aporta su último snapshot disponible en esa fecha o antes de ella. Capital actual propio debe coincidir con el capital conjunto derivado de esas aportaciones, en EUR y a la precisión acordada. No usar snapshots posteriores, incluir cuentas inactivas/no marcadas ni sumar varias observaciones de una misma cuenta. La ausencia de snapshot elegible no equivale a saldo cero: si impide comprobar el contrato mínimo, se aplica RF10. Esta es una regla de producto; no define algoritmo, almacenamiento de la fecha ni funciones.

**Ayuda sin doble conteo:** Ayuda familiar representa únicamente dinero externo previsto aún fuera de los saldos. Una vez depositado y reflejado en una cuenta, ese importe ya no puede figurar como ayuda pendiente. El campo conserva su separación respecto al ahorro propio; no se añade de nuevo al capital derivado de cuentas. Distinguir formalmente ayuda prevista/recibida con nuevos campos queda fuera de 002.

El contexto temporal de los valores sintéticos será explícito al preparar el dataset; elegir fechas concretas no requiere una nueva regla de negocio. No se implementa el cálculo ni se inventan fórmulas de financiación. El contrato no exige múltiples objetivos ni impide una extensión futura.

## Reglas de negocio y casos límite

| ID | Regla o caso | Resultado requerido o decisión pendiente |
| --- | --- | --- |
| RN01 | Persona o cuenta desconocida; titular incompatible | No aceptar el registro como válido. Informar del problema sin datos privados. |
| RN02 | Fecha inválida, campo obligatorio ausente o tipo fuera del conjunto permitido | No presentar los datos como conformes al contrato. No completar silenciosamente con valores inventados. |
| RN03 | Transferencia | Un único movimiento sin espejo entre cuentas existentes y distintas, incluso de personas diferentes. Persona es titular del origen. No modifica el patrimonio conjunto ni computa como ingreso o gasto. |
| RN04 | Signos y devolución | Todos los importes de movimientos son positivos. Ingreso suma al flujo, Gasto resta y Devolución suma compensando gasto; esta última sigue siendo un tipo distinto de Ingreso. |
| RN05 | Saldo cero o dato ausente | Cero es un dato válido; ausencia no es cero. Una colección vacía no equivale a un fallo de lectura. La demo entregada no puede omitir una de las cuatro entidades. |
| RN06 | Mes sin movimientos para una cuenta | No inventar movimientos ni deducir saldo cero. Los snapshots son observaciones explícitas; no se exige reconstruir todo el historial con movimientos. |
| RN07 | Cuenta inactiva con historial | Conservar la capacidad de resolver sus referencias históricas; no exigir generar este caso en la demo. |
| RN08 | Capital por encima de la meta o por debajo del inicial | No invalidarlo solo por esa comparación; no es una fórmula de progreso ni un simulador. |
| RN09 | Datos demo ausentes o dañados | Error comprensible sin fallback a Google ni petición de credenciales. No declarar carga válida si falta un dataset o el contrato mínimo falla; la forma técnica de validación se decide en PLAN. |

Las cuestiones A01–A04 están resueltas. No se implementan casos de prueba ni errores en esta tarea documental.

## Criterios de aceptación de la futura feature

Los siguientes escenarios son verificables al implementar y expresan decisiones confirmadas sin prescribir algoritmos. Ninguna prueba de aplicación se declara ejecutada aquí.

| ID | Dado / Cuando / Entonces | Cobertura |
| --- | --- | --- |
| CA01 | Dado un checkout limpio sin configuración privada ni cuentas externas, cuando se siguen las instrucciones de instalación y ejecución, entonces arranca la demo sin solicitar credenciales ni `secrets.toml`. | RF01–RF02 |
| CA02 | Dadas las dependencias instaladas y el acceso a Google bloqueado, cuando se inicia y utiliza la demo, entonces carga los datos locales sin depender de servicios Google. | RF02 |
| CA03 | Dada la demo iniciada, cuando el usuario accede a su vista inicial y la utiliza, entonces ve «Modo DEMO» y reconoce el carácter ficticio de sus datos. | RF03 |
| CA04 | Dado el conjunto incluido, cuando se inspeccionan las cuatro entidades, entonces todas están disponibles, los movimientos incluyen los cuatro tipos y ambas personas, existen al menos seis cuentas con las tres clases por persona y un objetivo vivienda con sus campos obligatorios. | RF04–RF07 |
| CA05 | Dados los movimientos, cuando se agrupan sus fechas por año y mes, entonces están representados seis meses. Diferencias de cantidad de movimientos entre meses no invalidan el conjunto. | RF05 |
| CA06 | Dado el conjunto demo, cuando se validan referencias, tipos y obligatoriedad, entonces todos los registros cumplen el contrato aclarado y ningún movimiento o saldo remite a una persona o cuenta inexistente. | RF08 |
| CA07 | Dados movimientos de los cuatro tipos, cuando se examinan sus importes y efectos definidos, entonces todos los importes son positivos, Ingreso suma, Gasto resta, Devolución compensa gasto y Transferencia tiene efecto patrimonial total cero, sin contarse como ingreso o gasto. | RF04, RF08 |
| CA08 | Dado un consumidor de las cuatro entidades, cuando obtiene datos demo mediante la capa común, entonces puede interpretarlos usando solo este contrato, sin conocer el formato original ni requerir configuración Google. No se necesita una segunda fuente real para comprobarlo. | RF09 |
| CA09 | Dado que falta un dataset, un campo obligatorio, hay una referencia inválida o no se cumple el contrato mínimo, cuando se intenta cargar la demo, entonces aparece un error comprensible y no se presenta la carga como válida, sin pedir Google ni exponer información privada. | RF10 |
| CA10 | Dado el conjunto demo y su procedencia documentada, cuando se revisan todos sus valores y el material publicado, entonces son sintéticos, solo aparecen Alex y Sam como personas y no hay información privada o copiada. | RP01–RP04 |
| CA11 | Dada la aplicación iniciada, cuando el usuario realiza el recorrido visible mínimo, entonces puede comprobar arranque correcto y carga de movimientos, cuentas, saldos y objetivos, sin dashboards finales. | RF11 |
| CA12 | Dado el objetivo «Compra vivienda» y cuentas con distintas marcas y estados, cuando se comprueba qué cuentas sustentan su capital propio, entonces solo participan las activas explícitamente marcadas y la ayuda familiar permanece separada del ahorro propio. Esto valida la selección conceptual, no un algoritmo de cálculo. | RF07–RF08 |
| CA13 | Dadas cantidades demo, cuando se revisa su unidad, precisión y presentación, entonces están en EUR con dos decimales y se muestra €, sin mezclar monedas. | RF04 |
| CA14 | Dado el catálogo de categorías y movimientos demo, cuando se comprueba su cobertura, entonces aparecen ejemplos de las trece categorías mínimas y los valores informados pertenecen al catálogo controlado. «Otros» admite los casos no previstos sin editar el catálogo durante el uso. | RF04 |
| CA15 | Dados movimientos con Ámbito informado, cuando se valida ese campo, entonces solo admite Personal o Común. Una Transferencia puede omitir Categoría y Ámbito sin resultar inválida por esas ausencias. | RF04 |
| CA16 | Dados varios snapshots de una cuenta en fechas distintas, cuando se comparan, entonces cada uno referencia a su titular y cuenta existentes y la fecha permite identificar el más reciente, sin exigir reconstrucción íntegra desde movimientos. | RF08 |
| CA17 | Dada una Transferencia, cuando falta una cuenta, alguna referencia no existe u origen y destino son la misma cuenta, entonces se detecta una infracción del contrato mínimo con error comprensible. | RF08, RF10 |
| CA18 | Dada la demo, cuando el usuario utiliza el recorrido disponible, entonces no dispone de operaciones para editar movimientos, cuentas, saldos u objetivos. | RF12 |
| CA19 | Dado cada tipo de movimiento, cuando se comprueban origen, destino y Persona, entonces cumple la matriz de cuentas y titularidad; un campo de cuenta no aplicable permanece vacío/null y una titularidad incompatible incumple el contrato. | RF04, RF08, RF10 |
| CA20 | Dada una transferencia ficticia Alex → Sam, cuando se examina su representación, entonces existe un único movimiento, Persona es Alex, origen pertenece a Alex y destino a Sam; no hay movimiento espejo ni alteración del patrimonio conjunto. | RF08 |
| CA21 | Dados movimientos de cada tipo, cuando se valida su clasificación, entonces Categoría es obligatoria salvo en Transferencia y Ámbito es obligatorio en Gasto/Devolución. En Ingreso/Transferencia puede ser vacío/null; si aparece es Personal o Común. Una Devolución permite reconocer el tipo de gasto compensado. | RF04 |
| CA22 | Dados snapshots positivos, cero y negativos en cualquier tipo de cuenta, cuando se valida el conjunto, entonces esos signos son admisibles; dos registros con igual Persona + Cuenta + Fecha infringen la unicidad y producen un error comprensible. | RF08, RF10 |
| CA23 | Dada la fecha de referencia demo y snapshots elegibles, antiguos y posteriores de cuentas participantes y no participantes, cuando se contrasta Capital actual propio, entonces coincide con las aportaciones del último snapshot no posterior de cada cuenta activa marcada, excluyendo el resto. | RF07, RF08 |
| CA24 | Dada ayuda externa pendiente no reflejada en saldos, cuando se revisa el objetivo, entonces permanece separada del capital de cuentas. Dada una cantidad ya depositada y reflejada en saldo, cuando se revisa la ayuda pendiente, entonces esa cantidad no se contabiliza otra vez. No se requiere editar datos ni crear campos de estado para comprobar ambos casos. | RF07, RF08 |

## Supuestos y límites conservados

Instalar dependencias puede requerir red; una vez instaladas, la demo no depende de Google ni de cuentas externas. No se presupone cierre diario, reconstrucción completa del historial ni fórmula de progreso del objetivo. Los valores y fechas concretos del dataset serán ficticios y explícitos; no son nuevas decisiones sobre el contrato.

## Resoluciones de CLARIFY

| Pregunta original | Resolución incorporada |
| --- | --- |
| Q01 — cobertura temporal | Resuelta: seis meses, sin exigir igual cantidad de movimientos por mes. No se añaden exigencias de continuidad ni de representación de ambas personas en cada mes que el usuario no haya pedido. |
| Q02 — moneda | Resuelta: EUR, símbolo €, dos decimales; multimoneda fuera de 002. |
| Q03 / A01 — signos, cuentas y transferencias | Resueltas: importes positivos y matriz por tipo. Persona es titular del destino en Ingreso/Devolución y del origen en Gasto/Transferencia. Se permiten transferencias entre personas, con un único movimiento sin espejo y sin efecto patrimonial conjunto. |
| Q04 / A02 — categoría y ámbito | Resueltas: catálogo mínimo y categoría opcional Transferencia entre cuentas. Categoría obligatoria salvo Transferencia; Ámbito Personal/Común obligatorio en Gasto/Devolución y opcional en Ingreso/Transferencia. Vacío/null permitido cuando no es obligatorio. |
| Q05 / A03 — saldos | Resueltas: snapshots explícitos positivos, cero o negativos, sin límites por tipo de cuenta; Persona + Cuenta + Fecha única y fechas sin hora. Sin reconstrucción completa obligatoria desde movimientos. |
| Q06 / A04 — vivienda | Resueltas: objetivo conjunto Compra vivienda; cuentas activas marcadas aportan su último snapshot no posterior a la fecha de referencia demo. Capital actual propio coherente con esas aportaciones; ayuda externa pendiente fuera de saldos, sin doble conteo de lo depositado ni nuevos campos de estado. |
| Q07 — recorrido y errores | Resuelta: Modo DEMO, arranque correcto y carga visible de las cuatro entidades; error comprensible cuando falla el contrato mínimo, nunca éxito silencioso. La presentación técnica y validación se decidirán en PLAN sin exigir un dashboard final. |

También queda confirmado el modo de solo lectura y el alcance excluido. No se exige ocultar todos los datos tras un error ni se autoriza presentarlos como una carga válida: el comportamiento mínimo aprobado es informar del incumplimiento sin éxito silencioso.

## Cuestiones abiertas restantes

No quedan ambigüedades de producto que impidan pasar a PLAN. A01–A04 se conservan arriba como resueltas. Se retiran las propuestas no aprobadas de cuenta origen receptora para ingresos, snapshots al cierre diario y límites no negativos para todos los capitales.

No se fijan frecuencia mínima adicional de snapshots, identificadores técnicos, formato, algoritmo de cálculo ni fechas concretas del dataset. PLAN concretará el diseño técnico respetando este contrato, sin ampliar los requisitos de producto. Tampoco se exige vinculación individual entre devolución y gasto ni nuevos campos para ayuda prevista/recibida.

## Cobertura de las funcionalidades futuras conocidas

| Necesidad prevista | Información habilitante y límite |
| --- | --- |
| Resumen y gastos | Fecha, tipo, importe en EUR, persona, categoría controlada y ámbito permiten agregación y filtros; la matriz por tipo fija su semántica. No se definen métricas o gráficos. |
| Ahorro y evolución | Tipo de cuenta, snapshots fechados y movimientos permiten analizar evolución sin prometer reconstrucción íntegra. La fórmula de ahorro mensual pertenece a su fase; transferencias no son ingreso ni gasto. |
| Objetivo vivienda | Meta, capitales, ayuda separada y cuentas activas participantes proporcionan la base; la fecha de referencia y la regla de ayuda pendiente evitan doble conteo. |
| Dashboards individuales | Persona y titularidad permiten separar Alex y Sam mediante los datos, sin fijar sus nombres en las páginas. |
| Simulador de compra | Capital propio y ayuda son información inicial potencial; precio, financiación, impuestos y demás entradas pertenecen a su futura spec, no a este dataset obligatorio. |
| Seguimiento de viviendas | Los registros de inmuebles, contactos, visitas y valoraciones quedan fuera de estas cuatro entidades y se especificarán en su fase. |

El contrato cubre la información de dominio solicitada a nivel conceptual, con la semántica necesaria para 002 cerrada. No se afirma que cierre todos los requisitos de las features futuras ni se crean entidades anticipadas para ellas.

## Revisión de CLARIFY

- **Constitución:** privacidad mediante procedencia sintética; independencia mediante contrato conceptual; demo sin Google; spec anterior al código; alcance mínimo; vocabulario explícito para mantenimiento; aceptación trazable a RF/RP. Sin modificación de arquitectura.
- **Separación QUÉ/CÓMO:** sin formato de archivos elegido, funciones, librerías, caché, credenciales, despliegue ni diseño de base de datos. La ruta del cargador solo referencia la frontera ya acordada.
- **Aceptación:** CA01–CA24 expresan resultados verificables, incluidos titularidad por tipo, transferencia única, clasificación, unicidad y signos de snapshots, referencia de capital y ausencia de doble conteo. No se presentan como pruebas de aplicación ejecutadas.
- **Roadmap:** solo modo demo de 002; Google real y dashboards permanecen en sus fases posteriores. Esta spec no altera sus estados.
- **Privacidad:** contenido original y conceptual, sin ejemplos tomados de finanzas reales.
- **Contradicciones revisadas:** se retiran los supuestos sustituidos por las resoluciones del usuario y se actualiza el modelo estable, eliminando su afirmación de que moneda y campos siguen sin decidirse. No hay conflicto con constitución, arquitectura o roadmap.
- **Preparación:** CLARIFY cerrado y spec preparada para PLAN. La feature sigue sin implementar ni completar. No hay plan, tareas ni implementación en esta entrega.
