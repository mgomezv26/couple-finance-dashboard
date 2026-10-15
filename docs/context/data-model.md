# Modelo de datos: contrato conceptual acordado

Se conoce el dominio general: información financiera de una pareja, procedente de una demo sintética o de una hoja del usuario. Los nombres Alex y Sam sirven solo para ejemplos ficticios, no establecen un modelo de usuarios o autenticación.

Se han acordado cuatro entidades conceptuales: movimientos (operaciones financieras), cuentas (titularidad, tipo y estado), saldos (snapshots fechados por cuenta) y objetivos (meta y capitales). Todavía no existen datasets ni implementación. No se ha diseñado una base de datos; Google Forms y Google Sheets son componentes del flujo, no entidades del dominio.

La [spec 002](../../specs/002-demo-data-source/spec.md) es la fuente de verdad de los requisitos, campos, obligatoriedad y criterios de aceptación de la demo. El contrato es independiente del formato y de la fuente. No inferir su esquema de proyectos externos o privados.

Hechos estables acordados para 002:

- Importes en EUR, símbolo €, precisión de dos decimales y fechas sin hora. Los importes de movimientos son positivos; su tipo determina el efecto financiero.
- Ingreso y Devolución utilizan cuenta destino; Gasto utiliza cuenta origen. Persona es titular de la cuenta afectada. Transferencia exige ambas cuentas y se atribuye al titular del origen; admite otra persona como titular del destino, usa un único movimiento sin espejo y no altera el patrimonio conjunto.
- Categoría es obligatoria salvo en Transferencia. Ámbito admite Personal/Común, es obligatorio en Gasto/Devolución y opcional en Ingreso/Transferencia. Los campos opcionales admiten vacío/null; la spec contiene el catálogo controlado y la matriz completa.
- Cada snapshot se identifica por Persona + Cuenta + Fecha, combinación única en demo. Su saldo puede ser positivo, cero o negativo sin restricciones por tipo de cuenta. No se presupone reconstrucción íntegra desde movimientos.
- El capital actual propio del único objetivo conjunto «Compra vivienda» es coherente con las cuentas activas marcadas para vivienda: cada una aporta su último snapshot disponible en la fecha de referencia demo o antes. Ayuda familiar representa dinero externo previsto aún fuera de los saldos; lo depositado no se cuenta también como ayuda pendiente.

La decisión de fuentes está en [ADR 0001](../adr/0001-demo-and-google-data-sources.md). Este resumen no fija almacenamiento, algoritmos ni extensiones futuras del modelo.
