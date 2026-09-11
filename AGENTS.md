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

## Tema visual Verdme Zen

La referencia visual es el tema `verdme-zen` de `psyco-web`.

### Principios

- Humano y clínico, no hospitalario.
- Ordenado y confiable, no burocrático.
- Seguro sin sentirse frío.
- Editorial, luminoso y con ritmo pausado.
- Light-first. La profundidad se crea con tonos, bordes y espacio, no con negro puro ni sombras pesadas.

### Tokens base

- Fondo papel: `#f3f6f2`.
- Fondo papel secundario: `#edf4ed`.
- Superficie: `#ffffff`.
- Sage suave: `#e4f2e9`.
- Sage medio: `#bddbc9`.
- Sage acción: `#327a51`.
- Sage acción oscuro: `#2b6645`.
- Sage profundo: `#1f4a34`.
- Texto principal: `#20251f`.
- Texto secundario: `#5f6b63`.
- Borde suave: `#e5e9e2`.
- Borde fuerte: `#cbd4ca`.
- Éxito: `#2f7a50`.
- Advertencia: `#b77a22`.
- Peligro: `#b65445`.

Los colores oficiales de Wompi se reservan para el módulo de co-marca y su reproducción visual. No deben contaminar la identidad general de Verdme.

### Tipografía

- Usar una familia sans del sistema compatible con el tema Zen: `-apple-system`, `BlinkMacSystemFont`, `SF Pro Display`, `Segoe UI`, `Roboto`, `Helvetica`, `sans-serif`.
- Pesos moderados. Reservar 700 para titulares importantes; evitar bloques completos en negrita.
- Titular principal fluido entre 2.6 y 4.8 rem, con interlineado compacto pero respirable.
- Texto de lectura entre 1 y 1.2 rem, con 1.55–1.75 de interlineado.
- No usar mayúsculas sostenidas salvo etiquetas breves con tracking amplio.

### Composición

- Ancho máximo general: 1180–1240 px.
- Diseñar primero para 360–430 px y escalar hasta escritorio.
- Secciones con 88–128 px verticales en escritorio y 64–80 px en móvil.
- Mantener grandes zonas de aire y alineación consistente.
- Usar radios de 14–18 px para controles y tarjetas; radios mayores solo en contenedores editoriales destacados.
- Preferir bordes suaves y sombras mínimas: `0 1px 2px rgba(31,42,35,.03)` o `0 18px 42px rgba(31,42,35,.07)`.
- No convertir cada contenido en una tarjeta. Alternar bloques editoriales, listas, superficies y demostraciones de producto.

### Componentes y estados

- CTA primario con fondo `#2b6645`, texto blanco, mínimo 48 px de alto y contraste AA.
- CTA secundario con fondo transparente o blanco y borde `#cbd4ca`.
- Links con foco visible de 2 px y offset de 3 px.
- Estados de producto usan color más texto o icono; nunca solo color.
- Controles táctiles de mínimo 44 × 44 px.
- Iconos lineales, sobrios y consistentes. No usar emojis como iconografía de interfaz.

### Imágenes y mockups

- Priorizar UI realista construida con HTML/CSS o capturas verificadas del producto.
- Los mockups ilustrativos solo muestran funciones presentes en `features.md`.
- No inventar métricas, nombres reales, historiales clínicos ni testimonios.
- Mantener el checkout aceptado de Wompi fiel a la referencia: monto `$120.000`, comercio “TU NOMBRE AQUÍ” y estructura completa de medios de pago.
- Los SVG de Wompi deben permanecer incrustados en el HTML; no adjuntarlos como archivos externos.
- Respetar proporciones, zona de seguridad y colores oficiales de Wompi.

## Accesibilidad y responsive

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

- La landing es estática y debe funcionar abriendo `index.html` o mediante un servidor estático.
- Evitar dependencias externas innecesarias.
- Mantener los recursos críticos locales o incrustados.
- No romper el módulo visual de Wompi ya aprobado.
- Preservar cambios del usuario no relacionados.

## Definición de terminado

Un cambio comercial está listo cuando:

1. Toda capacidad está respaldada por [features.md](./features.md).
2. La jerarquía conduce a un CTA principal sin distracciones.
3. El resultado visual se siente parte del tema Verdme Zen.
4. No hay emojis como iconos, claims absolutos ni promesas de IA no verificadas.
5. Funciona sin desbordes a 360, 390, 768, 1280 y 1440 px.
6. Teclado, foco, contraste, headings y landmarks son coherentes.
7. El checkout Wompi conserva monto, nombre, métodos y SVG incrustados.
8. `git diff --check` no reporta errores.
