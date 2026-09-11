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
- Mantener un CTA primario claro en navegación, hero y cierre; no competir con múltiples acciones equivalentes.

## Arquitectura del mensaje

Cada página debe construir el argumento en este orden:

1. **Resultado:** abrir con el cambio que la persona quiere sentir en su práctica.
2. **Contexto:** nombrar el costo de la dispersión sin dramatizar ni culpabilizar.
3. **Mecanismo:** explicar cómo Verdme conecta agenda, procesos, notas y cobros.
4. **Prueba de producto:** mostrar interfaces y flujos que existen en `main`.
5. **Diferenciador:** explicar con precisión la integración de cobros con Wompi.
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
- Evitar métricas, testimonios, logos de clientes, premios o sellos sin evidencia aprobada.
- Evitar resultados médicos, clínicos, legales o financieros garantizados.

## Fuente de verdad visual

La referencia visual de la landing es el paquete [`verdme-handoff-v0`](./verdme-handoff-v0/README.md). Debe traducirse a la landing como una gramática visual; no se debe copiar literalmente el HTML, el CSS, los datos ni los flujos del prototipo.

Consultar el paquete en este orden:

1. [`decisions/ui-direction.md`](./verdme-handoff-v0/decisions/ui-direction.md) para la intención y los principios visuales.
2. [`theme-draft/token-inventory.md`](./verdme-handoff-v0/theme-draft/token-inventory.md) para los tokens cromáticos de referencia.
3. [`prototype/index.html`](./verdme-handoff-v0/prototype/index.html) para comparar densidad, jerarquía, líneas y ritmo.
4. [`requirements/identity-brief-from-didier.md`](./verdme-handoff-v0/requirements/identity-brief-from-didier.md) para tipografía, iconografía, estados y accesibilidad.
5. [`decisions/implementation-boundaries.md`](./verdme-handoff-v0/decisions/implementation-boundaries.md) y [`decisions/ux-proposals.md`](./verdme-handoff-v0/decisions/ux-proposals.md) para distinguir estilo aprobado de propuestas que requieren revisión.

El handoff es una referencia de trabajo, no una identidad final ni una autorización para cambiar funcionalidades. Sus mocks no aprueban nuevas rutas, filtros, asociaciones, datos, APIs ni comportamientos. La landing solo adopta su dirección de estilo y debe seguir describiendo exclusivamente lo respaldado por `features.md`.

## Dirección visual Verdme v0

### Principios

- Humano, clínico, sobrio y claro; nunca hospitalario.
- Ordenado y confiable, no burocrático ni financiero.
- Editorial, luminoso y con ritmo pausado.
- Light-first. La profundidad se crea con tonos cálidos, líneas finas y espacio, no con negro puro ni sombras pesadas.
- El verde bosque funciona como acción, selección y señal; no como relleno dominante.
- La botánica aporta identidad de forma contextual y ocasional; no es decoración repetida ni iconografía para cada acción.
- La capa tecnológica se comunica mediante estructura, orden, señales y retículas sutiles; evitar la estética genérica de IA.

### Tokens base

- Fondo de aplicación: `#F6F6F3`.
- Superficie: `#FFFFFF`.
- Texto principal: `#242926`.
- Texto secundario: `#6C746E`.
- Verde principal: `#315B43`.
- Verde profundo: `#263C2E`.
- Selección suave: `#E2E7E0`.
- Verde de evento o señal suave: `#E2F0E5`.
- Línea suave: `#DFE4DE`.
- Línea de control: `#D8DCD7`.

Estos valores son la referencia vigente para la landing, pero el inventario del handoff sigue marcado como borrador. No inventar escalas adicionales ni presentar estos tokens como un `theme-delivery.json` definitivo. Para texto secundario que deba funcionar tanto sobre papel como sobre sage suave, usar la corrección accesible `#5F675F`, que conserva la intención del token y supera 4.5:1 en esas superficies. Los colores semánticos de éxito, información, advertencia y error deben conservar contraste y significado; no tomar como definitivos los valores ilustrativos del brief.

Los colores oficiales de Wompi se reservan para el módulo de co-marca y su reproducción visual. No deben contaminar la identidad general de Verdme.

### Tipografía

- La referencia tipográfica es **Bricolage Grotesque**, con pesos 400, 500 y 600, aplicada como una sola familia global.
- No cargar Google Fonts, CDN ni otra fuente remota. Bricolage Grotesque solo puede usarse cuando exista un WOFF2 local con licencia compatible y pueda incorporarse sin romper el carácter autocontenido de la landing.
- Mientras esa entrega esté pendiente, usar una única pila de sistema: `Arial`, `ui-sans-serif`, `system-ui`, `-apple-system`, `BlinkMacSystemFont`, `Segoe UI`, `sans-serif`.
- Usar pesos moderados. Reservar 600 para titulares y énfasis; evitar bloques completos en negrita y no introducir otra familia para títulos.
- Titular principal fluido entre 2.6 y 4.8 rem, con interlineado compacto, tracking negativo sutil y espacio suficiente.
- Texto de lectura entre 1 y 1.2 rem, con 1.55–1.75 de interlineado.
- No usar mayúsculas sostenidas salvo etiquetas breves con tracking amplio.

### Composición

- Ancho máximo general: 1180–1240 px.
- Diseñar primero para 360–430 px y escalar hasta escritorio.
- Secciones con 88–128 px verticales en escritorio y 64–80 px en móvil.
- Mantener grandes zonas de aire y alineación consistente.
- Usar radios moderados. Como referencia del prototipo: 5–6 px en controles, 9 px en secciones y hasta 12 px en modales; reservar círculos y pastillas para controles o estados que realmente lo necesiten.
- Priorizar divisores de 1 px y cambios sutiles de superficie. Las sombras deben ser mínimas y excepcionales, principalmente para capas flotantes.
- No convertir cada contenido en una tarjeta. Preferir secciones editoriales, listas lineales, superficies blancas y demostraciones de producto separadas por aire o líneas finas.
- Las retículas, patrones y señales tecnológicas deben permanecer tenues y subordinadas al contenido.

### Componentes y estados

- CTA primario con fondo `#263C2E`, texto blanco, mínimo 48 px de alto y contraste AA; `#315B43` puede usarse para hover, selección o señal según el contexto.
- CTA secundario con fondo transparente o blanco y borde `#D8DCD7`.
- Links, inputs y controles con foco visible de 2 px en `#315B43` y offset suficiente.
- Estados de producto usan color más texto o icono; nunca solo color.
- Controles táctiles de mínimo 44 × 44 px.
- Iconos lineales, sobrios y consistentes. No usar emojis como iconografía de interfaz.

### Imágenes y mockups

- Priorizar UI realista construida con HTML/CSS o capturas verificadas del producto.
- Los mockups ilustrativos solo muestran funciones presentes en `features.md`.
- No inventar métricas, nombres reales, historiales clínicos ni testimonios.
- Usar el prototipo del handoff para evaluar proporción, densidad y jerarquía; no reutilizar directamente su HTML, CSS, datos mock, caracteres Unicode ni recursos PNG como implementación o iconografía de sistema.
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
3. El resultado visual sigue la dirección Verdme v0 del handoff: fondo cálido, superficie blanca, verde bosque como señal, líneas finas, radios moderados y botánica contenida.
4. No hay emojis como iconos, ornamento botánico repetido, claims absolutos ni promesas de IA no verificadas.
5. Funciona sin desbordes a 360, 390, 768, 1280 y 1440 px.
6. Teclado, foco, contraste, headings y landmarks son coherentes.
7. El ejemplo ilustrativo de Wompi permanece idéntico en contenido, estructura y presentación interna.
8. `index.html` no referencia archivos CSS, JavaScript, imágenes o fuentes locales ni recursos remotos críticos.
9. `git diff --check` no reporta errores.
