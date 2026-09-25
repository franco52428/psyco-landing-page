# Lineamientos de producto, comunicación y diseño para la landing de Verdme

Este archivo es obligatorio para cualquier cambio dentro de este repositorio. Define cómo mantener una landing comercial, creíble y coherente con el producto real.

## Fuente de verdad del producto

Antes de redactar, diseñar o aprobar una sección, leer [features.md](./features.md).

- Solo promocionar capacidades verificadas allí.
- Cuando haya duda, revisar el `main` vigente de `psyco-web` y actualizar `features.md` antes de cambiar la landing.
- No convertir una idea, prototipo, rama o intención de roadmap en una promesa pública.
- No usar “factura” o “facturación” para las cuentas de cobro de Verdme.

## Audiencia y trabajo a resolver

La audiencia principal son psicólogos independientes y consultorios pequeños que necesitan continuidad entre lo clínico, lo administrativo y lo financiero.

La landing debe ayudarles a reconocer tres tensiones:

1. La información del consultorio queda dispersa entre agenda, notas, archivos y cobros.
2. El trabajo posterior a cada sesión compite con el tiempo y la energía clínica.
3. Cobrar y hacer seguimiento no debería romper la continuidad del proceso terapéutico.

La promesa central de Verdme es orden y continuidad: reunir la operación real del consultorio en un flujo sereno, trazable y bajo el criterio del profesional.

## Objetivo de conversión

El objetivo primario es que una persona interesada solicite acceso o una demostración. El objetivo secundario es que quien ya tiene cuenta pueda iniciar sesión.

- CTA primario: “Solicitar acceso” o “Conocer Verdme”.
- CTA secundario: “Iniciar sesión” o “Ver cómo funciona”.
- No decir “gratis”, “sin tarjeta”, “crear cuenta ahora” ni publicar precios sin una condición comercial vigente y documentada.
- Mantener un CTA primario claro en navegación y cierre; el hero presenta el producto y sus cuatro accesos internos sin botones adicionales.

## Arquitectura del mensaje

Cada página debe construir el argumento en este orden:

1. **Resultado:** abrir con el cambio que la persona quiere sentir en su práctica.
2. **Contexto:** nombrar el costo de la dispersión sin dramatizar ni culpabilizar.
3. **Mecanismo:** explicar cómo Verdme conecta agenda, procesos, notas y cobros.
4. **Prueba de producto:** mostrar interfaces y flujos que existen en `main`.
5. **Diferenciador:** explicar que el psicólogo puede recibir pagos de sus clientes online y gestionar los cobros desde Verdme.
6. **Confianza:** presentar controles de acceso y trazabilidad verificados, sin absolutos.
7. **Conversión:** cerrar con una invitación concreta y de bajo riesgo.

## Tono y enfoque publicitario

El tono es humano, sereno, directo y profesional.

- Hablar de “tú” con respeto y cercanía.
- Escribir frases cortas, concretas y fáciles de escanear.
- Priorizar beneficios operativos observables: menos dispersión, mayor continuidad, claridad sobre pendientes.
- Reconocer siempre el criterio y la responsabilidad del psicólogo.
- Evitar tecnicismos cuando una expresión cotidiana comunica mejor.
- Evitar grandilocuencia: “revolucionario”, “perfecto”, “la mejor”, “cambia vidas”, “garantizado”.
- Evitar lenguaje ansioso, hospitalario, bancario o corporativo.
- No caricaturizar la carga administrativa ni usar expresiones que resten seriedad al oficio.

## Reglas de copy

- Un encabezado debe comunicar una sola idea y, cuando sea posible, un resultado.
- El subtítulo explica el mecanismo; no repite el titular.
- Una tarjeta describe una capacidad real y su utilidad inmediata.
- No atribuir inteligencia, automatización o inferencia a funciones que dependen de acciones del usuario.
- “Dictado por voz” significa insertar texto hablado; no significa interpretar ni redactar clínicamente.
- “Compartir por WhatsApp” significa abrir el enlace listo para compartir; no significa envío automático.
- “Seguimiento de Wompi” se refiere a estados e información reportada por la integración.
- En la sección de pagos online, abrir con el beneficio: el psicólogo recibe pagos de sus clientes online y gestiona los cobros desde Verdme. El detalle puede explicar los distintos medios disponibles y la actualización automática de pagos y estados reportados en las finanzas de Verdme; no presentarlo como integración con contabilidad externa. Reservar la explicación del proveedor de pagos para el momento de habilitar la función; la marca puede permanecer en las vistas ilustrativas y el checkout aprobado. Usar links, saldos y estados como respaldo del beneficio, sin presentar el mensaje como una secuencia de pasos, insinuar que Verdme recibe fondos ni prometer registro de pagos fuera de lo reportado por la integración.
- En Seguridad, comunicar la protección en varios niveles: métodos de acceso para la cuenta, cifrado de los datos clínicos sensibles verificados en `features.md` y control de sesiones. La continuidad se expresa como información organizada para retomar el trabajo, sin prometer disponibilidad permanente, respaldos ni protección absoluta.
- Evitar métricas, testimonios, logos de clientes, premios o sellos sin evidencia aprobada.
- Evitar resultados médicos, clínicos, legales o financieros garantizados.

## Fuente de verdad visual

La identidad visual vigente de la landing es **Verdme Invierno**, el tema predeterminado `verdme-winter` de `psyco-web`. Consultar los tokens de `:root[data-theme="verdme-winter"]` y los tokens globales de tipografía, radios y sombras en [`../psyco-web/app/globals.css`](../psyco-web/app/globals.css). La fuente y su licencia están en [`../psyco-web/public/fonts/bricolage-grotesque/`](../psyco-web/public/fonts/bricolage-grotesque/). Si el tema cambia, revisar la implementación vigente antes de actualizar esta guía y después `index.html`.

El paquete [`verdme-handoff-v0`](./verdme-handoff-v0/README.md) conserva contexto histórico de producto y diseño. Sus valores cromáticos verde bosque, radios pequeños y prototipo visual ya no definen la identidad de la landing. Sus mocks no aprueban nuevas funcionalidades, rutas, datos ni comportamientos. Toda capacidad comercial sigue sujeta a `features.md`.

## Dirección visual Verdme Invierno

### Principios

- Humano, clínico, sobrio y claro; nunca hospitalario.
- Editorial y luminoso, con el mismo aire frío y sereno del producto.
- Base azul pizarra para navegación y acciones; superficies blanco hielo y grises verdosos para lectura y jerarquía.
- Líneas finas, cambios suaves de superficie y sombras discretas como en el producto.
- La botánica, si aparece, es contextual y ocasional; no sustituye la iconografía funcional.
- La capa tecnológica se comunica mediante estructura y retículas tenues, sin estética genérica de IA.

### Tokens base

- Fondo de aplicación y papel: `#F4F7F6`; superficie de lectura: `#FCFDFD`; tarjeta blanca: `#FFFFFF`.
- Papel frío más profundo: `#E5EBEA`; fondo del cuerpo: `#F8FAF9`.
- Texto principal: `#273031`; texto secundario: `#5D6C6D`.
- Acción y navegación profunda: `#26383A`; acción o selección media: `#465D60`; acento suave: `#8AA1A2`.
- Línea suave: `#DCE6E4`; línea marcada: `#B4C7C6`; borde de control: `#B8C9C8`.
- Selección suave: `#DCE8E7`; cubierta o bloque tenue: `#E8EFEE`.

Estos son roles de referencia tomados del tema invierno vigente en `psyco-web`, no un tema nuevo. Usar colores semánticos solo con el significado y contraste adecuados. Los colores oficiales de Wompi se reservan para el checkout ilustrativo.

### Tipografía

- Usar **Bricolage Grotesque Variable**, la fuente de `psyco-web`, con pesos 400, 500 y 600 y una sola familia para la landing.
- Incrustar en `index.html` los WOFF2 necesarios para el contenido en español como `data:` URI dentro de `@font-face`, con atribución SIL Open Font License 1.1. No cargar Google Fonts, CDN ni archivos de fuente separados. Mantener una pila de sistema como fallback.
- La tipografía interna del checkout de Wompi conserva su apariencia aprobada y queda excluida de la fuente global de la landing.
- Usar pesos moderados. Reservar 600 para titulares y énfasis; evitar bloques completos en negrita y no introducir otra familia para títulos.
- Titular principal fluido entre 2.15 y 2.8 rem en escritorio, y entre 2 y 2.25 rem en móvil, con interlineado compacto y tracking negativo sutil. Debe mantener una proporción equilibrada con la vista de producto y el resto del hero al 100% de zoom.
- Títulos de secciones comerciales entre 1.85 y 2.4 rem en escritorio, y entre 1.7 y 2 rem en móvil. Usar una misma escala en Procesos, Pacientes, Finanzas, Cobros, Seguridad y el cierre; conservar la tipografía propia de las vistas ilustrativas del producto.
- Texto de lectura entre 1 y 1.2 rem, con 1.55–1.75 de interlineado.
- No usar mayúsculas sostenidas salvo etiquetas breves con tracking amplio.

### Composición

- Ancho máximo general: 1180–1240 px.
- Diseñar primero para 360–430 px y escalar hasta escritorio.
- Secciones editoriales con 88–128 px verticales en escritorio y 64–80 px en móvil. Las demostraciones de producto que caben en un pantallazo pueden usar 32–52 px en escritorio y descontar la altura de la barra fija del alto visible.
- Mantener grandes zonas de aire y alineación consistente.
- En escritorio, la primera vista debe incluir el titular, la vista de producto y los cuatro accesos a agenda/procesos, notas, cobros y seguridad. Estos accesos deben enlazar a contenido existente dentro de la página.
- El menú principal sigue el orden real de la landing: Procesos clínicos, Pacientes, Finanzas, Pagos online y Seguridad. En tablet y móvil, ofrecer los mismos destinos en un menú nativo accesible sin JavaScript; mantener visible la acción de solicitar acceso.
- Cuando la altura de pantalla lo permita, el hero puede ocupar el alto visible y distribuir el aire alrededor del texto y la vista de producto; dejar que el contenido determine la altura en ventanas bajas, sin recortarlo.
- Usar los radios del producto como referencia: 14 px pequeño, 16 px medio, 18 px grande, 24 px amplio y 12 px para acciones. Reservar círculos y pastillas para controles o estados que los necesiten.
- Priorizar divisores de 1 px y cambios sutiles de superficie. Usar sombras suaves de baja opacidad para dar profundidad a elementos elevados.
- Alternar con sutileza papel frío y superficie blanco hielo entre módulos consecutivos, usando divisores finos para señalar el cambio sin fragmentar el recorrido.
- No convertir cada contenido en una tarjeta. Preferir secciones editoriales, listas lineales, superficies blancas y demostraciones de producto separadas por aire o líneas finas.
- Las retículas, patrones y señales tecnológicas deben permanecer tenues y subordinadas al contenido.

### Componentes y estados

- CTA primario con fondo `#26383A`, texto claro, mínimo 48 px de alto y contraste AA; `#465D60` puede usarse en hover y selección.
- CTA secundario con fondo `#FCFDFD` o transparente y borde `#B8C9C8`.
- Links, inputs y controles con foco visible de 2 px en `#465D60` y offset suficiente.
- Estados de producto usan color más texto o icono; nunca solo color.
- Controles táctiles de mínimo 44 × 44 px.
- Iconos lineales, sobrios y consistentes. No usar emojis como iconografía de interfaz.

### Imágenes y mockups

- Priorizar UI realista construida con HTML/CSS o capturas verificadas del producto.
- La vista ilustrativa de agenda del hero toma como referencia estructural [`img/agenda.png`](./img/agenda.png): marco de navegador, navegación lateral, cabecera, pestañas, selector de día, sesiones, estados, avisos y acciones. Conservar esa riqueza visual sin reutilizar nombres ni datos de la captura y sin depender del PNG para renderizar la landing.
- El encabezado de Agenda debe seguir el `PsycoContextHeader` de `psyco-web`: fondo Invierno, retícula tenue, línea de señal, título y descripción a la izquierda y hojas del recurso `public/images/patient-context-cover.png` a la derecha. Incrustar ese recurso en `index.html` para mantener la landing autocontenida.
- Escalar las hojas del encabezado con `background-size: auto 100%` y `background-position: right center`, como en la app. La línea de señal debe reservar a la derecha un ancho proporcional a 1,3 veces la altura del encabezado para no atravesar el área de hojas.
- En escritorio, presentar la vista ilustrativa en un marco 16:9 suficientemente amplio para reconocer la interfaz real. Ajustar la cantidad de filas visibles a ese formato sin cortar las acciones ni comprimir en exceso sus controles; en móvil, permitir más altura si hace falta para conservar legibilidad.
- Conservar el aire de la aplicación entre el encabezado contextual, las pestañas, los controles de fecha y la lista de sesiones al escalar el mock; no resolver el formato apilando estos bloques sin separación.
- En una sesión futura de esa vista, mostrar las acciones verificadas **Ver detalles**, **Reprogramar** y **Cancelar sesión**; mantenerlas legibles también cuando la vista se estrecha.
- En las acciones del mock de Agenda, **Editar/Reprogramar** usa el icono `SquarePen` y **Cancelar sesión** usa `Trash2`, como `SessionsDirectoryList` en `psyco-web`.
- Debajo del título de cada proceso en la lista de sesiones, mostrar los alias ficticios de los pacientes citados. Mantener las acciones de una sesión en la misma línea en escritorio cuando haya espacio suficiente.
- Procesos clínicos es el primer módulo destacado después del hero. Su demostración usa la vista real a escala: menú principal completo con Procesos clínicos activo, directorio de procesos, encabezado Invierno de `PsycoContextHeader`, pestañas y notas asociadas a sesiones. La cabecera reproduce el degradado, la retícula, la señal tenue que termina antes del libro, la jerarquía del título y la insignia compacta. El libro es `../psyco-web/public/images/processes/process-dossier-signal.png`, incrustado como `data:` URI para conservar el archivo único. La demostración debe dejar espacio suficiente para leer el mensaje en un pantallazo de escritorio. El mensaje usa un título y un solo párrafo centrados en conservar el contexto y la continuidad entre sesiones; las funciones verificadas en `features.md` sirven como respaldo breve, sin describir la pantalla paso a paso ni atribuir decisiones clínicas a la aplicación.
- La demostración de Pacientes sigue la composición real del producto: menú lateral, directorio con hojas y estados, encabezado contextual Invierno, pestañas, resumen de consentimiento y procesos vinculados. Construirla a escala con HTML/CSS, usar alias ficticios y adaptar sus paneles para móvil sin depender de una captura.
- La sección de Pacientes retoma la composición editorial del hero en espejo: demostración del producto a la izquierda y mensaje a la derecha en escritorio. Conservar la proporción y los espacios de la aplicación entre encabezado, pestañas, resumen y procesos al escalar la vista; en tamaños estrechos, apilar el texto antes de la demostración y simplificar el detalle interno para conservar legibilidad.
- La demostración de Finanzas va después de Pacientes y coloca el mensaje a la izquierda y la interfaz a la derecha en escritorio. Reproducir a escala el encabezado de Finanzas, estado de Wompi, resumen mensual y movimientos con datos ficticios coherentes. Explicar la automatización con precisión: el resumen se calcula a partir de registros y los estados de Wompi dependen de la integración; otros pagos requieren registro manual.
- La sección de pagos online debe presentar el mensaje y la demostración completos en un pantallazo de escritorio, considerando la barra fija. Ajustar el espacio exterior y escalar uniformemente el contenedor visual según la altura disponible; preservar el interior del checkout aprobado.
- En esa sección, el rótulo y el beneficio principal abren directamente el mensaje; no añadir una franja de logos Verdme–Wompi encima del titular.
- Mantener el bloque de pagos conciso: rótulo, titular, un párrafo y el checkout ilustrativo. No repetir el mensaje en una lista de beneficios debajo del párrafo.
- En las vistas ilustrativas de Agenda, Procesos clínicos, Pacientes y Finanzas, conservar el mismo menú principal de la aplicación: marca, cinco destinos, sección activa, Ajustes y Cerrar sesión, con proporciones y espaciados equivalentes al escalarlo.
- Los mockups ilustrativos solo muestran funciones presentes en `features.md`.
- No inventar métricas, nombres reales, historiales clínicos ni testimonios.
- Usar la interfaz real de `psyco-web` con el tema invierno como referencia para proporción, densidad y jerarquía. No reutilizar datos privados ni depender de capturas externas.
- Si aparecen Pacientes, Procesos o Agenda, conservar su lenguaje visual diferenciado: hojas suaves para personas, señal estructurada para procesos y datos en primer plano para agenda. No repetir estos motivos como ornamento general de todas las secciones.
- Todo icono operativo debe ser SVG lineal, usar `currentColor`, mantener una geometría consistente y estar incrustado en `index.html`.

### Regla de oro: ejemplo ilustrativo de Wompi

El ejemplo ilustrativo del caso de pago con Wompi está aprobado y es inmutable. Ningún cambio de estilo, refactor o ajuste responsive puede modificar su contenido o presentación interna.

- No cambiar su HTML, copy, monto `$120.000`, comercio “TU NOMBRE AQUÍ”, concepto, textos auxiliares, medios de pago, orden ni marcas representadas.
- No cambiar sus SVG incrustados, colores oficiales, tipografía interna, proporciones, espaciado, radios, sombras, distribución, tamaños ni comportamiento responsive.
- No sustituir sus símbolos, logos o recursos visuales ni aplicarles los tokens generales de Verdme.
- Se puede ajustar únicamente el contenedor exterior de la sección de cobros para integrarlo con la landing, siempre que el ejemplo `.wompi-checkout` y todos sus descendientes permanezcan visual y estructuralmente idénticos.
- Si una regla general entra en conflicto con esta excepción, prevalece la preservación exacta del ejemplo de Wompi.

## Accesibilidad y responsive

### Regla de oro: diseño multidispositivo

Todo cambio debe diseñarse y validarse para móvil, tablet y escritorio desde el inicio. Una versión de escritorio reducida no cuenta como experiencia responsive terminada.

- Diseñar la composición base para 360–430 px y adaptarla deliberadamente a 768, 1280 y 1440 px.
- Reordenar, apilar, simplificar u ocultar detalle secundario cuando el espacio cambie; no limitarse a reducir tipografía o escalar toda la interfaz.
- Mantener jerarquía, legibilidad, CTA, navegación y contexto de producto en cada tamaño.
- Evitar scroll horizontal, texto recortado, controles superpuestos y zonas táctiles menores de 44 × 44 px.
- Los mockups deben conservar texto útil legible; en móvil se simplifican antes de comprimirse.
- Probar estados de foco, zoom al 200%, contenido largo y saltos de línea en todos los rangos relevantes.
- El ejemplo ilustrativo de Wompi también debe comprobarse en cada tamaño, pero permanece sujeto a su regla de preservación exacta: si presenta un problema, se reporta antes de modificar su interior.

- HTML semántico: un solo `h1`, jerarquía de encabezados y landmarks claros.
- Todo texto debe seguir legible a 200% de zoom.
- Ninguna sección debe producir scroll horizontal a 360 px.
- Imágenes y visuales deben usar `max-width: 100%` y escalar con su contenedor.
- Los mockups complejos deben simplificarse o escalarse de forma controlada en móvil, sin texto ilegible.
- Navegación accesible por teclado, foco visible y etiquetas `aria` donde hagan falta.
- Respetar `prefers-reduced-motion`.
- No usar movimiento continuo ni animaciones que bloqueen la lectura.

## SEO y metadatos

- Título específico y menor a aproximadamente 60 caracteres.
- Descripción clara de 140–160 caracteres basada en capacidades reales.
- `lang="es"`, viewport y color de tema definidos.
- El contenido esencial debe existir en HTML sin depender de JavaScript.

## Restricciones de implementación

- La landing es un artefacto estático autocontenido: debe funcionar cargando únicamente `index.html` desde S3 y CloudFront.
- Todo el CSS debe permanecer dentro de etiquetas `<style>` en `index.html`; no crear hojas de estilo externas.
- Todo SVG, icono o recurso visual necesario debe estar incrustado en `index.html`.
- No agregar JavaScript, fuentes, imágenes, hojas de estilo ni recursos críticos que dependan de una ruta local adicional.
- Evitar dependencias externas y llamadas de red durante el render inicial.
- No copiar literalmente el HTML o CSS de `verdme-handoff-v0/prototype/` ni inferir funcionalidad desde sus mocks.
- No romper el módulo visual de Wompi ya aprobado.
- Preservar cambios del usuario no relacionados.

## Definición de terminado

Un cambio comercial está listo cuando:

1. Toda capacidad está respaldada por [features.md](./features.md).
2. La jerarquía conduce a un CTA principal sin distracciones.
3. El resultado visual sigue Verdme Invierno de `psyco-web`: papel frío, superficie blanco hielo, texto azul pizarra, navegación profunda, selección gris verdosa, líneas finas y radios del producto.
4. No hay emojis como iconos, ornamento botánico repetido, claims absolutos ni promesas de IA no verificadas.
5. Funciona sin desbordes a 360, 390, 768, 1280 y 1440 px.
6. Teclado, foco, contraste, headings y landmarks son coherentes.
7. El ejemplo ilustrativo de Wompi permanece idéntico en contenido, estructura y presentación interna.
8. `index.html` no referencia archivos CSS, JavaScript, imágenes o fuentes locales ni recursos remotos críticos.
9. `git diff --check` no reporta errores.
