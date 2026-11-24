# Golden rules de diseño y mantenibilidad

Versión común: 1. Fecha: 2026-11-06. Solicitud expresa del usuario para todos los proyectos Psyco. Esta es la normativa local de ingeniería; se aplica junto con las reglas de dominio, seguridad, pruebas y entrega del proyecto. Catálogo: [design-pattern-catalog.md](design-pattern-catalog.md).

## Alcance y proporcionalidad

- Aplica al código nuevo, código modificado y refactors autorizados: backend, frontend, scripts y herramientas. No obliga a introducir orientación a objetos en SQL, documentos legales, proyecciones financieras, contenido editorial o artefactos gráficos.
- Respetar las restricciones específicas: HTML autocontenido aprobado puede organizarse por secciones internas sin externalizar recursos; migraciones históricas, archivos generados y ejemplos visuales inmutables no se reescriben para satisfacer métricas.
- El diseño se demuestra con responsabilidades, contratos y código; un nombre terminado en Strategy, Factory, Manager o Service no acredita un patrón ni SOLID.
- La profundidad de documentación se ajusta al riesgo. Un cambio local sencillo puede justificar reutilización y ausencia de patrón adicional en un párrafo; un flujo con varias etapas, variantes o efectos requiere la matriz y secuencia siguientes. No crear arquitecturas ceremoniales para cambios triviales.
- Estas reglas no autorizan refactors ajenos, migraciones, workers, secretos, dependencias, cambios de pipeline ni despliegues. Mantener las autorizaciones y el orden de pruebas vigentes en cada proyecto.

## DESIGN-001 — Diseñar responsabilidades antes de implementar

1. Planner identifica el caso de uso, invariantes, consumidores, variantes reales y puntos de cambio; inventaría implementaciones reutilizables con rutas verificadas. No se limita a enumerar archivos que hay que tocar.
2. Architect cierra responsables, dependencias, contratos de entrada/salida, secuencia y alternativas. La unidad elegida puede ser una función, módulo, componente o clase según el contexto.
3. Para flujos con varios pasos se registra el orquestador y cada delegado, sus efectos y la frontera de transacción/reintento. Distinguir llamadas síncronas de trabajo asíncrono.
4. Task Planner deriva tareas por responsabilidad y frontera verificable. Una tarea no puede dejar la elección de patrón o ubicación para resolverla improvisadamente al implementar.
5. Implementer aplica ese diseño o devuelve una desviación material a arquitectura. Reviewer contrasta el mapa con las unidades reales, no solo con la descripción.

Matriz mínima para un diseño no trivial:

| ID | Responsabilidad/cambio real | Unidad y ruta | Contrato/dependencias | Reutilización | Patrón o solución simple y razón | Evidencia de cierre |
| --- | --- | --- | --- | --- | --- | --- |
| D-01 | Una responsabilidad identificable | Archivo y función/clase/componente | Entrada, salida, errores y efectos | Pieza existente o motivo de nueva | Alternativas pertinentes, coste y decisión | Código y validación aplicable |

## SOLID-001 — Principios aplicados a contratos y responsabilidades

| Principio | Exigencia comprobable en Psyco |
| --- | --- |
| S — Responsabilidad única | Agrupar lo que cambia por una misma razón de negocio; separar responsabilidades independientes. No equivale a una clase por método ni a separar líneas arbitrariamente |
| O — Abierto/cerrado | Aislar variaciones reales detrás de puntos de extensión acotados; evitar repetir la misma selección de variante en varios módulos. No prohíbe modificar código existente ni exige anticipar futuras variantes |
| L — Sustitución | Implementaciones del mismo contrato conservan precondiciones, resultados, errores e invariantes. Una variante no puede conceder más acceso, romper idempotencia o cambiar el significado de éxito |
| I — Segregación de interfaces | Contratos pequeños según necesidades del consumidor; evitar interfaces enormes con métodos no aplicables, no-op o excepciones de método no soportado |
| D — Inversión de dependencias | El caso de uso depende de contratos de negocio en las fronteras variables; adapters/repositorios encapsulan SDK, transporte y persistencia. Usar la inyección/composición existente, sin service locator global |

Las funciones y módulos también cumplen estos principios: no se exige crear una jerarquía de clases para utilizarlos. Mantener encapsulación, alta cohesión y dependencias explícitas sin ciclos. Compartir contexto mediante parámetros/objetos tipados; no mediante estado global mutable, singleton con usuario actual o lectura implícita del request desde cualquier capa.

## SIMPLICITY-001 — KISS, DRY, YAGNI y composición

- KISS: elegir la solución más pequeña que preserve invariantes y sea fácil de seguir; reducir niveles de indirección y estados. Código compacto pero opaco no es simple.
- DRY: una regla de negocio tiene una autoridad clara. Buscar reutilización antes de copiar el flujo de pago, validación o acceso. Código parecido con significados distintos no se unifica a la fuerza.
- YAGNI: implementar variaciones del alcance vigente, no frameworks de plugins, motores de reglas o proveedores especulativos. Documentar una futura extensión no autoriza construirla.
- Preferir composición y delegación a herencia para compartir capacidades. Herencia solo con sustitución válida; no usar clases base universales para ocultar ramas de negocio.
- Un helper debe tener nombre, dominio y consumidor claros. Evitar archivos utils/helpers/manager de responsabilidades inconexas y fragmentación en funciones triviales que solo añaden saltos sin encapsular conocimiento.
- Separar cálculos/decisiones puras de efectos cuando reduzca acoplamiento. Cada método mantiene un nivel de abstracción coherente y usa nombres declarativos del dominio.

## ORCHESTRATION-001 — Orquestador legible y delegados acotados

Un caso de uso de varios pasos debe poder leerse como una secuencia de acciones de negocio. El orquestador coordina orden, contratos, errores y política transaccional; los delegados realizan tareas concretas. No mezclar en él HTTP/SDK, SQL/ORM, cifrado, selección de identidad, cálculos, plantillas y notificaciones.

Ejemplo ilustrativo de responsabilidades para un pago, no código que deba copiarse ni diseño cerrado de suscripciones:

```text
ProcesarEventoDePago
  1. Leer pago canónico mediante el adapter existente.
  2. Resolver y validar a qué contrato pertenece.
  3. Aplicar resultado mediante la frontera transaccional existente:
       registrar el pago/histórico;
       aplicar período y vigencia solo cuando corresponda;
       registrar el trabajo derivado que deba salir del commit.
  4. Devolver un resultado tipado; procesar capacidades derivadas
     mediante el mecanismo vigente de ejecución/reconciliación.
```

- No reabrir commits separados por delegado si esos cambios deben ser atómicos. Si el repository actual controla la transacción, conservar esa frontera y extraer solo colaboradores compatibles con ella; no introducir otra Unit of Work por estética.
- La extracción no altera ownership, estados aprobados/rechazados, cálculo de períodos, auditoría, idempotencia, orden, contratos o reintentos. No conceder licencia por una aceptación de tarjeta ni por una notificación sin consulta canónica.
- Cuando hay pasos asíncronos, hacer explícito qué está comprometido y qué está pendiente. Outbox/inbox, saga o compensación solo si el problema los requiere y reutilizando lo existente; no equivalen a crear workers nuevos automáticamente.
- Orquestador/delegados es una organización de responsabilidades, no obligación de microservicios ni un nombre GoF. Evitar un megaorquestador que conozca todos los casos de la aplicación.

## PATTERN-001 — Elegir por problema, no por catálogo

El [catálogo ampliado](design-pattern-catalog.md) contiene familias y alternativas; no es una lista que haya que implementar completa. Para cada variación o frontera relevante, el diseño registra problema, alternativas pertinentes, solución elegida, contrato, costes y condiciones para revisarla. Registrar «función/módulo existente sin patrón adicional» es válido si resuelve el caso y está razonado.

- Strategy encapsula comportamiento intercambiable; Factory crea/ensambla productos. Un resolver que selecciona instancias ya inyectadas no se vuelve Factory por nombrarlo así.
- Una simple condición exhaustiva es válida para variantes pequeñas y cohesionadas. Cuando las ramas tienen reglas/efectos independientes o se repiten, resolver la variación una vez y delegar mediante un contrato común.
- Una nueva interfaz se justifica por una frontera, sustitución o consumidor real, no por reproducir todas las clases con su interfaz gemela.
- Diferenciar nivel de diseño: GoF, arquitectura, persistencia, integración, resiliencia y presentación no son intercambiables. Una saga no sustituye una transacción local; CQRS no exige event sourcing; Observer no garantiza entrega duradera.
- El patrón conserva reglas de seguridad/privacidad. No usar una variante para hacerse pasar por otro actor, omitir autorizaciones o reutilizar datos de otro contexto.

## SIZE-001 — Tamaño y complejidad como señales de revisión

Umbrales internos orientativos para código escrito a mano: archivo mayor de 400 líneas físicas, función/método mayor de 60 líneas, más de tres niveles de control anidados o más de cinco parámetros independientes. Son disparadores de revisión, no definiciones universales de SOLID ni un gate automático de cantidad de líneas.

Ante un umbral o responsabilidad múltiple, exigir una de estas resoluciones en la evidencia: extraer una responsabilidad cohesiva, simplificar o justificar con alcance/contrato y revisión independiente por qué mantenerlo es más claro. No aprobar crecimiento opaco sin esa resolución. No compactar código, moverlo a archivos part1/part2 o crear wrappers sin responsabilidad para evadir el umbral.

Excepciones explícitas: generado, datos/fixtures declarativos, snapshots, tablas de traducción, migraciones históricas inmutables, código de terceros y artefactos autocontenidos por requisito. En HTML/CSS/JS autocontenido, revisar la responsabilidad lógica de secciones/controladores aunque no se pueda separar físicamente el archivo. Las pruebas también requieren claridad; el volumen de casos no justifica mezclar dominios.

Un archivo heredado grande no bloquea por sí solo un cambio pequeño ni autoriza refactorizarlo entero. Evaluar las unidades tocadas y efectos causales; no agregar responsabilidades inconexas. Los umbrales admiten justificación técnica revisada dentro del alcance, sin requerir autorización adicional del usuario por una elección rutinaria de diseño.

## REFACTOR-001 — Refactor incremental con comportamiento preservado

1. Precisar la frontera, invariantes y comportamiento observable que se preserva, con evidencia vigente o caracterización proporcional al riesgo conforme a las reglas de pruebas del proyecto.
2. Extraer responsabilidad/contrato y mantener la entrada pública; no cambiar reglas de negocio, errores, efectos o presentación por aprovechar el refactor.
3. Validar la pieza extraída y consumidores afectados con evidencia de comportamiento, no solo tests que comprueban el nuevo número de llamadas privadas. Comparar variantes con el mismo contrato y verificar efectos/errores relevantes.
4. Preservar transacciones, idempotencia, concurrencia, datos, seguridad, cachés y compatibilidad. No migrar de framework, sustituir el pipeline ni reestructurar otros módulos sin necesidad del alcance.
5. Retirar duplicación obsoleta del cambio cuando sus consumidores ya estén migrados y comprobados; no mantener dos autoridades permanentes de una regla. Separar refactor de evolución funcional para que el diff se pueda revisar.

## DESIGN-REVIEW-001 — Evidencia y control de fase

| Fase | Evidencia obligatoria aplicable |
| --- | --- |
| Planner | Riesgos de mantenibilidad, invariantes, variantes reales y reutilización; profundidad de diseño requerida |
| Architect | Mapa de responsabilidades/contratos, selección de patrones, secuencia de orquestación y límites de efectos/consistencia |
| Task Planner | Cada tarea enlaza responsabilidad, unidad, dependencias, escenario y criterio de cierre |
| Implementer/Fixer | Mapa diseño → rutas y funciones reales, extracciones/reutilización, desviaciones y justificaciones de complejidad |
| Reviewer | Revisión del código y contratos por un contexto distinto; hallazgos por regla, evidencia y resolución; detectar falsa delegación y sobreingeniería |
| Tester/QA/Release | Comprobar comportamiento, sustitución y efectos del alcance; adoptar evidencia vigente, respetar calendario local de automatización y no afirmar calidad de diseño solo por tests verdes |

- Plan, arquitectura, tareas, notas de implementación y reporte de revisión conservan el mismo diseño vigente. Ante desvío material actualizar la fase dueña antes de continuar; no llenar retrospectivamente una tabla para aparentar aprobación.
- Si falta una decisión/evidencia aplicable o el código contradice el diseño dentro del alcance, la fase no puede aprobarse hasta resolverlo con el gate vigente. Hallazgos heredados ajenos siguen el registro de deuda del dueño; no amplían el refactor.
- La revisión identifica unidades reales, motivo de cambio y dependencia/evidencia. Un encabezado, una checklist marcada o contar líneas no demuestra cumplimiento. El gate determinista existente comprueba estructura según su alcance; el juicio de diseño se verifica semánticamente, sin fingir un validador nuevo o pruebas no ejecutadas.
- Para cambios puramente documentales/de contenido, justificar diseño de código n/a. No crear interfaces, tests de producto, infraestructura o simulaciones para cumplir una casilla.

## Fuentes y naturaleza de la norma

Los criterios de aplicación a Psyco y los umbrales son decisiones internas de esta guía. Las fuentes fundamentan conceptos, alternativas y riesgos; no constituyen un mandato de aplicar todos los patrones ni de migrar de stack.

- [Robert C. Martin: responsabilidad única](https://blog.cleancoder.com/uncle-bob/2014/05/08/SingleReponsibilityPrinciple.html).
- [Microsoft: principios arquitectónicos, separación, encapsulación y dependencias](https://learn.microsoft.com/en-us/dotnet/architecture/modern-web-apps-azure/architectural-principles).
- [The Pragmatic Programmer: consejos de los autores](https://pragprog.com/tips/).
- [Martin Fowler: YAGNI](https://martinfowler.com/bliki/Yagni.html) y [Dependency Injection](https://martinfowler.com/articles/injection.html).
- [Google Engineering Practices: revisión de diseño, complejidad y pruebas](https://google.github.io/eng-practices/review/reviewer/looking-for.html).
- [Martin Fowler: Service Layer](https://martinfowler.com/eaaCatalog/serviceLayer.html) y [Unit of Work](https://martinfowler.com/eaaCatalog/unitOfWork.html).
- [React: reutilización de lógica con custom hooks](https://react.dev/learn/reusing-logic-with-custom-hooks).
- Familias, fuentes y alternativas ampliadas en el catálogo local enlazado al inicio.

Esta actualización de normativa no certifica que el código previo ya cumpla estas reglas ni ejecuta refactors o pruebas de producto. Las copias locales de esta edición se distribuyen juntas entre los proyectos principales para poder leerse sin otro checkout; un cambio común posterior debe sincronizar su versión y revisar divergencias sin sobrescribir reglas locales.
