# Catálogo ampliado de patrones y alternativas de diseño

Versión común: 1. Fecha: 2026-11-06. Complementa [engineering-design-rules.md](engineering-design-rules.md), en particular PATTERN-001. Son 79 entradas de selección: los 23 patrones GoF y alternativas de arquitectura, dominio, datos, integración, resiliencia y presentación. No es un inventario exhaustivo de la disciplina ni una lista de implementaciones existentes en Psyco.

## Cómo utilizarlo

1. Partir del problema, contratos, variaciones y efectos reales; no del nombre favorito de un patrón.
2. Leer la familia pertinente y comparar las opciones que resuelven ese problema, incluida una función/módulo simple o la reutilización existente.
3. Documentar ID, motivo, unidad concreta, contrato, costes y alternativa descartada. En problemas pequeños basta una justificación breve; no evaluar las 79 entradas en cada feature.
4. Verificar fuentes primarias/documentación del patrón concreto cuando sea nuevo o la garantía sea relevante. Las filas son criterios internos de selección; no reemplazan el estudio de transacciones, seguridad o concurrencia del caso.
5. La implementación demuestra la decisión mediante estructura y comportamiento. Tipar una interfaz no garantiza sustitución; renombrar un servicio no implementa un patrón.

## Creacionales GoF

| ID | Patrón | Cuándo considerarlo | Coste, límite o motivo para evitarlo |
| --- | --- | --- | --- |
| GOF-C-01 | Factory Method | La creación del producto debe variar mediante un punto de extensión polimórfico | No confundir con cualquier función constructora; no introducir herencia solo para escoger dos instancias inyectadas |
| GOF-C-02 | Abstract Factory | Se necesitan familias coherentes de colaboradores que deben combinarse entre sí | Exceso si solo existe un producto variable; vigilar proliferación de familias |
| GOF-C-03 | Builder | Construcción con varias opciones/invariantes o etapas que deben producir un objeto válido | Preferir constructor/objeto tipado para configuraciones simples; no permitir estados parcialmente válidos expuestos |
| GOF-C-04 | Prototype | Crear variantes copiando una configuración/estructura existente costosa de montar | Definir copia superficial/profunda; no clonar identidades, secretos o referencias transaccionales |
| GOF-C-05 | Singleton | Recurso único con alcance y lifecycle justificados; aprovechar el contenedor existente | No almacenar usuario/IPS actual en estado global ni reemplazar DI con acceso estático |

## Estructurales GoF

| ID | Patrón | Cuándo considerarlo | Coste, límite o motivo para evitarlo |
| --- | --- | --- | --- |
| GOF-S-01 | Adapter | Traducir una API/protocolo externo al contrato local | No filtrar SDK, errores o payloads del proveedor al dominio |
| GOF-S-02 | Bridge | Dos dimensiones evolucionan de manera independiente, por ejemplo operación y transporte | No crear dos jerarquías si solo cambia una dimensión pequeña |
| GOF-S-03 | Composite | Árbol de elementos con operaciones uniformes sobre hoja y grupo | No imponer la misma semántica a objetos que no son sustituibles |
| GOF-S-04 | Decorator | Añadir capacidades transversales manteniendo contrato y composición | Orden y observabilidad explícitos; no esconder autorización, cobros o commits |
| GOF-S-05 | Facade | Entrada reducida y estable a un subsistema con varios colaboradores | No convertirla en un servicio universal con reglas de todos los dominios |
| GOF-S-06 | Flyweight | Muchísimos objetos comparten estado inmutable y hay coste medido | Separar estado contextual; evitar complejidad por una optimización hipotética |
| GOF-S-07 | Proxy | Controlar acceso/lifecycle a un recurso remoto, diferido o protegido | Hacer visibles latencia, fallos y permisos; no presentar IO como lectura gratuita |

## De comportamiento GoF

| ID | Patrón | Cuándo considerarlo | Coste, límite o motivo para evitarlo |
| --- | --- | --- | --- |
| GOF-B-01 | Chain of Responsibility | Etapas de manejo con orden y criterio explícito de continuar/detener | No perder pasos obligatorios ni esconder quién termina la cadena |
| GOF-B-02 | Command | Representar una intención ejecutable con datos y responsable claros | No exige command bus ni cola; undo y reintento necesitan semántica propia |
| GOF-B-03 | Iterator | Recorrer colecciones sin exponer representación o paginación interna | Respetar cursores, memoria, límites y cierre/cancelación del recurso |
| GOF-B-04 | Mediator | Coordinar colaboraciones de varios componentes con interacción circular | No centralizar todo el negocio en un mediador omnisciente |
| GOF-B-05 | Memento | Restaurar estado local sin exponer detalles internos | Controlar tamaño y datos sensibles; no confundir con historial financiero o auditoría inmutable |
| GOF-B-06 | Observer | Notificar cambios a suscriptores con acoplamiento reducido | Suscripción/desuscripción y errores claros; no garantiza entrega duradera o transacción |
| GOF-B-07 | State | Comportamiento y transiciones varían por estados con reglas relevantes | Un enum con tabla de transiciones puede bastar; no crear una clase por estado simple |
| GOF-B-08 | Strategy | Algoritmos/políticas reales intercambiables bajo un contrato | Contratos y errores equivalentes; una condición local pequeña puede ser más clara |
| GOF-B-09 | Template Method | Secuencia estable con pasos especializados y sustitución válida | Usa herencia; preferir composición cuando las variantes o pasos cambian independientemente |
| GOF-B-10 | Visitor | Operaciones nuevas sobre estructura de tipos estable | Coste alto cuando cambian los tipos; no introducirlo para una discriminated union pequeña |
| GOF-B-11 | Interpreter | Gramática acotada que necesita interpretar expresiones del dominio | No construir un lenguaje/motor genérico si bastan configuración tipada y validaciones |

## Arquitectura, dominio y organización de casos de uso

| ID | Alternativa | Cuándo considerarla | Coste, límite o motivo para evitarla |
| --- | --- | --- | --- |
| ARC-01 | Transaction Script | Operación de negocio sencilla expresable como procedimiento claro | Extraer responsabilidades al crecer; no duplicar el mismo proceso en varios endpoints |
| ARC-02 | Application Service / orquestador | Caso de uso con pasos y colaboradores definidos | Coordina; no absorbe SDK, SQL, cálculos y todas las variantes |
| ARC-03 | Domain Model | Invariantes/comportamientos de negocio suficientemente ricos | No crear entidades anémicas ceremoniales para un CRUD pequeño |
| ARC-04 | Arquitectura en capas | Separar entrada, aplicación/dominio y persistencia según el stack | Evitar capas pasantes sin responsabilidad y respetar contratos existentes |
| ARC-05 | Ports and Adapters | Aislar negocio de proveedores, transporte o persistencia variables | Puertos por consumidor/frontera real, no interfaz gemela de cada clase |
| ARC-06 | Vertical Slice | Agrupar un caso de uso y sus cambios de extremo a extremo | Compartir reglas estables; no duplicar infraestructura o saltar capas de seguridad |
| ARC-07 | Modular Monolith | Módulos de dominio separados dentro del despliegue actual | Fronteras e imports controlados; no llama microservicio a cada carpeta |
| ARC-08 | Value Object | Identidad por valor, validación y comportamiento inmutable | No encapsular todo primitivo si no aporta invariantes o significado |
| ARC-09 | Aggregate / Aggregate Root | Frontera de invariantes y consistencia de un conjunto de entidades | Evitar agregados gigantes o transacciones entre dominios sin justificación |
| ARC-10 | Specification | Predicados de negocio combinables con significado estable | No traducir arbitrariamente a SQL ni perder alcance/ownership al componer |
| ARC-11 | Policy | Encapsular una decisión variable de negocio o autorización | No sustituye el enforcement ni justifica un motor de reglas genérico |
| ARC-12 | Anti-Corruption Layer | Proteger el modelo local de semánticas incompatibles de otro sistema | Mantener traducción y propietario claros; no duplicar el dominio entero |

## Datos, persistencia y evolución

| ID | Alternativa | Cuándo considerarla | Coste, límite o motivo para evitarla |
| --- | --- | --- | --- |
| DATA-01 | Repository | Acceso a agregados/datos con operaciones del dominio | Evitar repositorio genérico que exponga ORM o permita omitir ownership |
| DATA-02 | Data Mapper | Separar representación persistida de objetos del dominio | Reutilizar mapping/ORM existente; no añadir mapeos idénticos sin motivo |
| DATA-03 | Active Record | Modelo sencillo que integra representación y persistencia | Solo donde el proyecto lo admita; no reemplaza la arquitectura Repository vigente de las API |
| DATA-04 | Unit of Work | Coordinar cambios que deben compartir commit/rollback | Reutilizar la transacción existente; no abrir commits independientes en delegados |
| DATA-05 | Identity Map | Una representación por entidad dentro de una unidad de trabajo | Limitar lifecycle; no caché global que mezcle usuarios, IPS o versiones |
| DATA-06 | Query Object | Consulta compleja con filtros/orden reutilizables y tipados | Igual alcance en lista/conteo; evitar miniORM o composición insegura de SQL |
| DATA-07 | CQRS | Lecturas y comandos requieren modelos/contratos diferentes | No exige buses, servicios separados o event sourcing; no duplicar por moda |
| DATA-08 | Materialized View / proyección | Lecturas/agregados repetidos con coste medido | Definir actualización, reconciliación y frescura; no presentar datos atrasados como actuales |
| DATA-09 | Event Sourcing | Reconstrucción por eventos es una necesidad explícita del dominio | Exige versionado/replay/privacidad; no confundir con guardar logs o auditoría |
| DATA-10 | Concurrencia optimista | Detectar actualizaciones sobre versiones obsoletas | Versiones y conflicto explícitos; reintentar solo cuando conserva intención |
| DATA-11 | Bloqueo pesimista | Invariante concurrente exige serialización localizada | Orden, timeout y duración acotados; no mantener locks mientras se llama a proveedores |
| DATA-12 | Expand/Contract | Evolución compatible de schema/contratos con versiones coexistentes | No retirar estructura antes de migrar consumidores y verificar datos |

## Integración, mensajes y evolución entre sistemas

| ID | Alternativa | Cuándo considerarla | Coste, límite o motivo para evitarla |
| --- | --- | --- | --- |
| INT-01 | Gateway | Entrada local al servicio externo con semántica del dominio | Contrato, errores y credenciales encapsulados; no un proxy abierto de cualquier API |
| INT-02 | Publish/Subscribe | Varios consumidores independientes reaccionan a hechos | Definir entrega, orden y privacidad; no garantiza coherencia inmediata |
| INT-03 | Inbox / deduplicación | Mensajes pueden repetirse y sus efectos no deben duplicarse | Recepción durable PENDING antes de procesar es válida. Marcar PROCESSED junto al efecto local; efectos externos exigen idempotencia/reconciliación. No descartar pendientes por existir su ID |
| INT-04 | Transactional Outbox | Cambio local y publicación/trabajo derivado deben persistir juntos | Entrega repetible requiere consumidores idempotentes y reconciliación; no promete exactly-once |
| INT-05 | Saga orquestada | Proceso distribuido necesita varios commits y compensaciones | No sustituye transacción local; compensar no equivale a rollback perfecto |
| INT-06 | Choreography | Reacciones distribuidas con autonomía y causalidad observable | Evitar ciclos, eventos secretos y procesos imposibles de seguir |
| INT-07 | Process Manager | Correlacionar pasos, respuestas y tiempos de un proceso prolongado | Persistir avance y manejo de fallos; exceso para tres llamadas síncronas |
| INT-08 | Content-Based Router | Elegir destino/manejador según información validada del mensaje | Selección central y tipada; no autorización basada en campos no confiables |
| INT-09 | Aggregator | Reunir respuestas/eventos de un conjunto conocido | Definir completitud, duplicados, timeout y resultados parciales |
| INT-10 | Competing Consumers | Distribuir trabajos independientes con claim exclusivo y reintentos | Requiere idempotencia y límites; no paralelizar operaciones con orden obligatorio |
| INT-11 | Backend for Frontend | Clientes diferentes requieren contratos agregados distintos | No duplicar reglas de negocio ni trasladar autorización al frontend |
| INT-12 | Strangler Fig | Migrar incrementalmente una frontera hacia implementación nueva | Criterios de cutover/reversa y retirada; no mantener dos fuentes de verdad indefinidamente |
| INT-13 | API Composition | Componer consultas de varios servicios sin copiar el dominio | Controlar latencia y fallos; no revelar datos de otro ámbito al agregar |

## Resiliencia, carga y coordinación

| ID | Alternativa | Cuándo considerarla | Coste, límite o motivo para evitarla |
| --- | --- | --- | --- |
| RES-01 | Timeout / deadline / cancelación | Una operación externa o larga necesita presupuesto acotado | Cancelar la espera no demuestra que un cobro remoto no ocurrió |
| RES-02 | Retry con backoff y jitter | Fallo transitorio y operación segura/idempotente | No reintentar cobros o escrituras ciegamente; presupuesto y resultado incierto explícitos |
| RES-03 | Circuit Breaker | Dependencia con fallos repetidos genera sobrecarga | Recuperación/estado observables; no fallback que conceda permisos o invente pagos |
| RES-04 | Bulkhead | Aislar capacidad de una dependencia o categoría de trabajo | Pools/límites medidos; no complejidad sin contención demostrada |
| RES-05 | Rate Limiting | Limitar abuso o preservar recursos con una clave de alcance correcta | Definir respuesta y consistencia; no usar una clave que mezcle identidades |
| RES-06 | Queue-Based Load Leveling | Absorber picos con procesamiento diferido permitido | Cola no vuelve inmediato el resultado; definir backpressure y retención |
| RES-07 | Cache-Aside | Lecturas costosas admiten frescura e invalidación definidas | No reutilizar positivos de autorización/licencia contra reglas de revocación; incluir contexto en clave |
| RES-08 | Single Flight / coalescing | Solicitudes simultáneas idénticas causan trabajo redundante | Clave por ámbito y manejo de cancelación; no mezclar resultados privados |
| RES-09 | Leader Election | Tarea realmente distribuida requiere un coordinador por período | Reutilizar tecnología probada; no implementar consenso artesanal para un job local |
| RES-10 | Lease y fencing token | Un propietario temporal puede seguir actuando tras perder exclusividad | El recurso debe rechazar tokens obsoletos; un lock con TTL por sí solo no basta |

## Presentación y composición de interfaz

| ID | Alternativa | Cuándo considerarla | Coste, límite o motivo para evitarla |
| --- | --- | --- | --- |
| UI-01 | MVC | Framework separa entrada, modelo y representación | Seguir convenciones locales; no imponer MVC clásico sobre App Router |
| UI-02 | MVVM / Presentation Model | Estado de presentación y comandos necesitan separación comprobable | No duplicar estado del dominio ni añadir una capa solo por nombrarla |
| UI-03 | Container / Presentational | Separar coordinación/carga de una vista con responsabilidad clara | Evitar props enormes y wrappers sin trabajo propio |
| UI-04 | Custom Hook | Compartir lógica React con lifecycle y entradas/salidas concretos | Comparte lógica, no automáticamente estado; no esconder todos los efectos en un mega-hook |
| UI-05 | Reducer / máquina de estados | Interacciones y transiciones relacionadas crecen en combinaciones | Estado mínimo y transiciones explícitas; no reducer global para toda pantalla |
| UI-06 | Compound Components | Varias piezas UI colaboran dentro de una API de composición estable | Contexto acotado, accesibilidad y uso fuera del contenedor definidos |
| UI-07 | Controlled / Uncontrolled | Elegir quién es autoridad de estado de un control | No mantener dos autoridades ni cambiar de modo incidentalmente |
| UI-08 | Render Props / slots | Variación de presentación con lógica estable y composición necesaria | Reutilizar primitivas del proyecto; no API genérica difícil de entender |
| UI-09 | Colocación de estado y datos derivados | Mantener estado cerca del consumidor y calcular valores reproducibles | No duplicar estado derivable ni copiar lógica de autorización del servidor |

## Ejemplos de selección por problema Psyco

| Problema observado | Opciones que comparar | Evidencia que decide |
| --- | --- | --- |
| Un mismo pago puede financiar una práctica o una IPS | Función/resolver acotado, Policy, Strategy, Service Layer | Variantes reales, contratos equivalentes, misma semántica de pago y autorización por contexto |
| Construir integraciones con diferentes dependencias | DI/composición existente, función factory, Factory Method o Abstract Factory | Construcción/lifecycle diferentes; no basta seleccionar una instancia ya existente |
| Flujo largo mezcla proveedor, DB, período y notificación | Orquestador con delegados, Adapter/Gateway, Repository y transacción/outbox existentes | Secuencia legible y preservación de commit, historial, idempotencia y estados |
| Página mezcla render, red, validación y efectos | Componentes con responsabilidades, custom hooks, reducer cuando proceda | Contratos UI, estados mínimos, accesibilidad y protección server/client conservadas |
| Varias respuestas financieras para perfiles diferentes | Proyecciones/DTOs y Policy/CQRS solo si aporta | Lista permitida de datos en servidor; no enviar el resumen completo para ocultarlo en UI |
| Archivo heredado enorme | Extract Function/Class/Module, mover responsabilidad, eliminar indirección inútil | Cambio autorizado delimitado, consumidores y regresión caracterizados, sin división mecánica |

## Fuentes y ampliación

La clasificación GoF utiliza el [catálogo del autor de Refactoring.Guru](https://refactoring.guru/design-patterns/catalog), y la descripción de [Interpreter](https://sourcemaking.com/design_patterns/interpreter), con distinción de [Strategy](https://refactoring.guru/design-patterns/strategy) y [Factory Method](https://refactoring.guru/design-patterns/factory-method). Los criterios de aplicación y precauciones de las tablas son recomendaciones internas para Psyco, no transcripciones ni garantías de esas fuentes.

Fuentes primarias y documentación técnica de las otras familias:

- [Martin Fowler y colaboradores: catálogo de arquitectura empresarial](https://martinfowler.com/eaaCatalog/).
- [Unmesh Joshi: catálogo de sistemas distribuidos](https://martinfowler.com/articles/patterns-of-distributed-systems/).
- [Microsoft Architecture Center: patrones y tradeoffs](https://learn.microsoft.com/en-us/azure/architecture/patterns/).
- [Documentación de transactional outbox](https://docs.aws.amazon.com/prescriptive-guidance/latest/cloud-design-patterns/transactional-outbox.html).
- [React: custom hooks y reutilización](https://react.dev/learn/reusing-logic-with-custom-hooks).
- [Google: diseño y complejidad en revisión](https://google.github.io/eng-practices/review/reviewer/looking-for.html).

El catálogo es extensible: un patrón adicional registra problema, fuente primaria, alternativas, coste, responsabilidad y criterio verificable antes de adoptarlo. No convertir un catálogo ampliado en permiso para aumentar el alcance, dependencias, infraestructura o acceso de nube. Los proyectos documentales/SQL/estáticos aplican solo las alternativas pertinentes y preservan sus restricciones específicas.
