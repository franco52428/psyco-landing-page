# Entrega de identidad visual para Psyco

## Propósito

Este documento se entrega al equipo de diseño. Define exactamente qué debe
entregarse para sustituir la iconografía actual y aplicar una identidad visual
completa sin que el equipo de desarrollo modifique cada pantalla. Cada SVG se
convertirá en un componente React con el mismo nombre que Psyco ya usa.

Ejemplo: el archivo Save.svg se convierte en el icono que hoy se importa como
Save. No se cambiará ningún import en las pantallas.

## Entrega de tema de identidad

Psyco ya soporta temas de apariencia. Actualmente persiste una preferencia
visual no sensible, aplica el id del tema al atributo data-theme del documento y
sobrescribe tokens globales bajo un selector de tema. El diseño debe entregar
un paquete de tokens, no CSS por ruta ni una imagen que desarrollo deba copiar
a mano.

El paquete de un tema nuevo se recibe en esta estructura:

    psyco-web/assets/custom-themes/verdme-alba/
      theme-delivery.json
      README-license.md
      fonts/
        AlbaSans-Variable.woff2
      previews/
        dashboard-1440x900.png
        dashboard-390x844.png
        login-390x844.png
        notes-1440x900.png
        states-1440x900.png

Los nombres alba y AlbaSans son ejemplos, no una decisión de producto. El
identificador real debe tener el formato verdme-nombre-en-kebab-case. La carpeta
de entrega no activa el tema por sí sola: desarrollo la convierte en tokens
globales, registra el id y valida browser/build. Esto evita aplicar un cambio
visual parcial o romper la hidratación de la app.

### Archivo obligatorio: theme-delivery.json

Entregar un único JSON válido, UTF-8, sin comentarios y con los valores finales
en hexadecimal de seis caracteres. El siguiente es un ejemplo de estructura
completa; sus valores son ilustrativos:

    {
      "id": "verdme-alba",
      "labels": {
        "es": "Alba",
        "en": "Dawn",
        "pt": "Alvorada",
        "fr": "Aube",
        "de": "Morgendämmerung",
        "it": "Alba"
      },
      "mode": "light",
      "replaceExistingTheme": null,
      "font": {
        "family": "Alba Sans",
        "fallback": "ui-sans-serif, system-ui, sans-serif",
        "files": [
          {
            "path": "fonts/AlbaSans-Variable.woff2",
            "weight": "400 700",
            "style": "normal",
            "license": "README-license.md"
          }
        ]
      },
      "colors": {
        "background": "#F8F7F2",
        "foreground": "#252821",
        "paper": { "50": "#F8F7F2", "100": "#F1EFE7" },
        "surface": "#FFFFFF",
        "sage": {
          "100": "#E6EFE7",
          "300": "#BED5C0",
          "500": "#5F8062",
          "700": "#3D6042",
          "900": "#263D2B"
        },
        "ink": { "700": "#5F665D", "900": "#252821" },
        "line": { "soft": "#E3E4DC", "strong": "#C9CDC3" },
        "control": {
          "selected": "#3D6042",
          "selectedForeground": "#FFFFFF",
          "border": "#D2D5CE",
          "surface": "#FFFFFF"
        },
        "info": { "50": "#EEF6FF", "200": "#C6DEF6", "600": "#2F659F", "700": "#25527F" },
        "success": { "50": "#EEF8F0", "200": "#C8E5CC", "500": "#4E8A5A", "700": "#306B3A" },
        "warning": { "50": "#FFF7E9", "500": "#A97024" },
        "danger": { "50": "#FFF1EE", "200": "#F3C4BC", "500": "#B65748", "700": "#8F4036" }
      },
      "radii": {
        "sm": "14px",
        "md": "16px",
        "lg": "18px",
        "xl": "24px",
        "action": "12px"
      },
      "shadows": {
        "card": "0 1px 2px rgb(37 40 33 / 0.03)",
        "soft": "0 18px 42px rgb(37 40 33 / 0.07)"
      },
      "icons": {
        "defaultStrokeWidth": 1.85,
        "sizeScale": "keep-current"
      },
      "pwa": {
        "themeColor": "#F8F7F2",
        "backgroundColor": "#F8F7F2"
      },
      "contrast": {
        "normalTextMinimum": "4.5:1",
        "largeTextMinimum": "3:1",
        "controlAndFocusMinimum": "3:1"
      }
    }

No omitir una llave del ejemplo. Si un valor no cambia respecto al tema base,
debe declararse explícitamente con su valor final; nunca usar un texto como
same as current. Esto permite revisar, automatizar la validación y evitar
herencias accidentales.

### Cómo se aplicará el paquete

| Entrega de diseño | Destino técnico existente | Resultado |
| --- | --- | --- |
| id y labels | lib/themes.ts y lib/i18n.ts | El tema aparece como opción válida con nombre localizado. |
| colors, radii y shadows | Selector :root con data-theme en app/globals.css | Cards, controles, fondos, bordes y estados se actualizan sin CSS local por pantalla. |
| family y archivos WOFF2 | Carga local de fuente en app/layout.ts y variables globales de fuente | Una única familia global; ningún componente elige fuente propia. |
| icon sizeScale y stroke | Variables de tamaño y PsycoIcon existentes | La nueva iconografía conserva proporción y estados. |
| pwa | lib/app-metadata.ts y manifest | Solo se actualiza si el tema se convierte en la identidad por defecto. |
| previews y contrast | Browser validation, Gherkin y pruebas visuales | Desarrollo compara el resultado con la entrega aprobada. |

No entregar CSS, clases Tailwind, HTML, componentes React ni una especificación
por ruta. El equipo técnico traduce el JSON a los tokens semánticos existentes
para que una misma identidad se aplique al sistema completo.

### Tipografía y licencia

1. Proponer una sola familia principal legible para textos clínicos y operativos.
   No usar una fuente distinta para cada página, card o título.
2. Entregar WOFF2 local para todos los pesos y estilos que el diseño exige. Se
   recomienda una variable font normal con rango de pesos; si no existe,
   entregar un WOFF2 por peso utilizado.
3. Adjuntar README-license.md con licencia, titular, URL de compra/descarga,
   alcance de uso web y confirmación de que Psyco puede distribuirla.
4. Incluir fallbacks del sistema. No usar una fuente remota, una URL de Figma o
   un CDN como requisito para renderizar el producto.
5. Mantener texto de interfaz en una escala cómoda. La fuente no puede basar su
   legibilidad en trazos ultrafinos ni tracking excesivo.

### Paleta, estados y accesibilidad

El tema es light-first: cálido, humano, tranquilo y clínico sin frialdad. No
proponer negro puro dominante, colores corporativos saturados, morados por
defecto, fondos hospitalarios, sombras pesadas ni una experiencia financiera.

La entrega debe incluir un par de color para cada estado:

| Estado | Fondo | Texto/icono | Borde/foco | Condición |
| --- | --- | --- | --- | --- |
| Base | paper/surface | ink | line soft | Lectura continua y tarjetas. |
| Acción primaria | sage 700 | paper 50 | sage 900 | Default, hover y disabled. |
| Selección/foco | control selected | selectedForeground | sage 500 | Visible por teclado, no solo por color. |
| Éxito | success 50 | success 700 | success 200 | Confirmación tranquila. |
| Advertencia | warning 50 | ink 900 | warning 500 | Sin alarma agresiva. |
| Error | danger 50 | danger 700 | danger 200 | Claro, humano y accionable. |
| Información | info 50 | info 700 | info 200 | Diferenciada de éxito/error. |

Medir y adjuntar el contraste de cada par. El mínimo es 4.5:1 para texto
normal, 3:1 para texto grande y 3:1 para componentes gráficos, bordes y foco.
No redondear un resultado por debajo del umbral. Estas condiciones siguen
[WCAG 2.2 para contraste de texto](https://www.w3.org/WAI/WCAG22/Understanding/contrast-minimum.html)
y [contraste no textual](https://www.w3.org/WAI/WCAG22/Understanding/non-text-contrast.html).

### Previews y estados que debe entregar diseño

Entregar previews exactos en los tamaños de la carpeta propuesta:

1. Dashboard autenticado en 1440 por 900 y 390 por 844.
2. Login o registro en 390 por 844.
3. Directorio de pacientes o sesiones en 1440 por 900.
4. Notas en 1440 por 900; esta ruta conserva su experiencia de lector
   independientemente del tema.
5. Una lámina de estados con input, select, botón, card, chip, modal y menú en
   default, hover, focus-visible, disabled, error, loading, empty y success.
6. Una lámina de la nueva iconografía sobre surface, sage, danger y selección.

Los previews describen el objetivo visual; no sustituyen las pruebas reales
sobre la aplicación. Si se propone reemplazar un tema existente, marcar
replaceExistingTheme con su id y obtener aprobación explícita de producto. Si
no existe esa aprobación, se agrega un tema nuevo y se preservan verdme-calm,
verdme-landing y verdme-zen.

## Dónde entregar los archivos

La carpeta fuente oficial será:

    psyco-web/assets/custom-icons/source/

La carpeta es plana: no crear subcarpetas por categoría. Entregar exactamente
un archivo SVG por icono. Si debe moverse la carpeta en el futuro, desarrollo
cambia únicamente sourceDirectory en:

    psyco-web/custom-icons.config.mjs

No modificar imports de la aplicación, componentes, archivos de configuración
de Next, TypeScript o Jest. Esos archivos apuntarán automáticamente al
adaptador de iconos.

## Nombres y extensión: regla estricta

1. Usar exactamente los nombres indicados en el catálogo obligatorio de este
   documento. El sistema distingue mayúsculas y minúsculas.
2. Usar extensión .svg en minúscula.
3. El nombre del archivo debe ser el identificador más .svg. Por ejemplo:

       Activity.svg
       CalendarPlus2.svg
       ChartNoAxesCombined.svg
       UserRoundSearch.svg

4. No usar variantes como activity.svg, Save-24.svg, SaveOutlined.svg,
   save.svg, Save.svg.svg ni archivos con espacios.
5. No entregar PNG, JPG, WebP, PDF, AI, EPS, Figma export link ni un sprite.
   El asset operativo es solamente SVG individual. Las fuentes de diseño
   adicionales pueden entregarse en un paquete separado, fuera de esta carpeta.
6. No agregar, omitir ni renombrar assets sin que desarrollo actualice primero
   el manifiesto y este instructivo.

## Especificación visual y técnica del SVG

Cada SVG debe cumplir todas estas condiciones:

| Aspecto | Condición obligatoria |
| --- | --- |
| Artboard | 24 por 24 unidades. |
| Root | Debe usar viewBox exactamente 0 0 24 24. No incluir width, height, class ni style en el SVG raíz. |
| Color | Usar currentColor. No usar hexadecimal, rgb, hsl, gradientes, variables CSS, opacidad de color fija ni imágenes. |
| Estilo base | Iconografía lineal, sobria y terapéutica; no corporativa, fría, agresiva ni decorativa. |
| Relleno | Por defecto fill none. Un relleno intencional solo usa currentColor y debe aprobarse como excepción de diseño. |
| Trazo | El trazo debe heredarse del SVG raíz: no declarar stroke-width en paths, lines, circles u otras formas. El sistema controla ese valor. |
| Terminaciones | Usar stroke-linecap round y stroke-linejoin round en el SVG raíz, salvo una excepción explícita aprobada. |
| Espacio seguro | Mantener al menos 2 unidades de margen visual respecto al borde del viewBox. No recortar puntas, círculos ni sombras. |
| Geometría | Vectores limpios y escalables; sin rasterización, máscara, filtro, blur ni sombra. |
| Animación | No incluir animate, animateTransform, SMIL, CSS animation ni GIF. |
| Texto | No convertir un nombre, letra o número en parte del icono mediante una fuente externa. Si hay forma vectorial aprobada, debe ser path. |

El sistema aplica en runtime los siguientes valores. Por eso el SVG no debe
fijarlos localmente:

| Prop del sistema | Efecto esperado en el asset |
| --- | --- |
| size | Cambia ancho y alto del SVG de forma proporcional. |
| color | Cambia todo trazo o relleno basado en currentColor. |
| strokeWidth | Cambia el grosor de todos los trazos. |
| className | Permite estados visuales de la app, incluidos hover, focus y disabled. |
| aria, role, focusable | Conserva accesibilidad del control que contiene al icono. |

## Seguridad y contenido prohibido

El validador rechazará cualquier SVG que contenga:

- script o atributos de evento, como onclick;
- foreignObject, iframe, object, embed, audio o video;
- image, raster embebido, data URL o referencias HTTP/HTTPS;
- use que haga referencia a contenido externo;
- doctype, entidades XML o comentarios con instrucciones ejecutables;
- style, CSS inline, filtros, máscaras, clipPath, patrones o gradientes;
- logos de terceros, material con licencia no compatible o elementos que
  requieran atribución no aprobada.

No comprimir los SVG de forma que convierta currentColor o la geometría
aprobada en valores no legibles. El equipo de desarrollo ejecutará la validación
automática al recibir el paquete.

## Control de calidad antes de entregar

1. Verificar cada icono a 16 px, 20 px, 24 px y 32 px sobre fondo claro.
2. Comprobar que el color puede ser negro suave, verde sage y rojo de error sin
   perder contraste ni fijar un color local.
3. Comparar flechas, chevrons, iconos de calendario, estados, edición y
   reproducción como familias coherentes.
4. Revisar pares opuestos: Eye/EyeOff, Play/Pause/Square, ChevronLeft/
   ChevronRight, TrendingUp/TrendingDown, PanelLeftOpen/PanelLeftClose y
   FolderOpen/FolderClosed.
5. Entregar el set completo en una sola revisión. Un solo SVG faltante bloquea
   el cambio global de la aplicación.
6. Adjuntar para revisión el catálogo visual de psyco-ux-ideas/iconos.html; es
   la referencia de nombres y de iconos actualmente usados, no la fuente final
   de diseño.

## Catálogo obligatorio: 109 nombres

Entregar estos 109 archivos, exactamente una vez:

    Activity.svg
    AlertTriangle.svg
    Archive.svg
    ArrowLeft.svg
    ArrowRightLeft.svg
    Bell.svg
    Bold.svg
    Brain.svg
    BriefcaseMedical.svg
    CalendarCheck2.svg
    CalendarClock.svg
    CalendarDays.svg
    CalendarOff.svg
    CalendarPlus.svg
    CalendarPlus2.svg
    CalendarRange.svg
    CalendarSearch.svg
    CaseSensitive.svg
    ChartNoAxesCombined.svg
    Check.svg
    ChevronDown.svg
    ChevronLeft.svg
    ChevronRight.svg
    ChevronUp.svg
    ChevronsUpDown.svg
    CircleAlert.svg
    CircleCheck.svg
    CircleDollarSign.svg
    CircleHelp.svg
    CircleOff.svg
    CircleStop.svg
    ClipboardPaste.svg
    ClipboardPenLine.svg
    Clock3.svg
    Copy.svg
    Download.svg
    EllipsisVertical.svg
    Eraser.svg
    ExternalLink.svg
    Eye.svg
    EyeOff.svg
    FileCheck2.svg
    FileImage.svg
    FilePlus2.svg
    FileStack.svg
    FileText.svg
    Filter.svg
    Fingerprint.svg
    FolderClock.svg
    FolderClosed.svg
    FolderOpen.svg
    FolderPlus.svg
    FolderSearch.svg
    Gift.svg
    Globe2.svg
    HandCoins.svg
    Highlighter.svg
    Info.svg
    Italic.svg
    KeyRound.svg
    Layers3.svg
    LayoutDashboard.svg
    Link2.svg
    List.svg
    ListChecks.svg
    ListOrdered.svg
    ListPlus.svg
    LoaderCircle.svg
    LockKeyhole.svg
    LogOut.svg
    Menu.svg
    Mic.svg
    Minus.svg
    Package.svg
    Palette.svg
    PanelLeftClose.svg
    PanelLeftOpen.svg
    Paperclip.svg
    Pause.svg
    PauseCircle.svg
    Pencil.svg
    Play.svg
    Plus.svg
    Quote.svg
    RotateCcw.svg
    Save.svg
    Search.svg
    Settings.svg
    Shield.svg
    ShieldAlert.svg
    ShieldCheck.svg
    Square.svg
    SquarePen.svg
    TextCursorInput.svg
    Trash2.svg
    TrendingDown.svg
    TrendingUp.svg
    TriangleAlert.svg
    Underline.svg
    Undo2.svg
    UserRound.svg
    UserRoundPlus.svg
    UserRoundSearch.svg
    UserX.svg
    Users.svg
    UsersRound.svg
    Volume2.svg
    WalletCards.svg
    X.svg

## Qué hará desarrollo al recibir la entrega

1. Colocar los SVG en la carpeta indicada sin modificar nombres.
2. Ejecutar pnpm icons:check. Si falla, devolver al diseñador el nombre y la
   regla exacta que necesita corrección.
3. Generar los exports React y ejecutar pruebas de props, tamaño, color, trazo
   y accesibilidad.
4. Validar la aplicación en desktop y móvil antes de automatizar regresiones.
5. Ejecutar los gates de calidad y solo entonces activar la fuente local para
   todos los imports existentes.
6. Si se entregó un tema, validar primero el manifiesto, licencia, contraste y
   previews; integrar sus tokens globales y comprobar una recarga con la
   preferencia del tema guardada.

## Contacto de cambios

Para pedir un icono nuevo, una variante rellena o modificar la semántica de uno
existente, no crear un archivo alterno. Solicitar primero la actualización del
manifiesto de esta feature. Así el nombre, el asset, la cobertura y el catálogo
permanecen sincronizados.

## Handoff

- phase_status: pass
- highest_severity: none
- next_phase: Implementer
- blocking_reason: n/a
- required_inputs_for_next_phase: Set completo de SVG bajo estas condiciones y,
  si se aprueba una identidad nueva, el paquete de tema completo indicado arriba.
- rules_evaluated: DOC-001, DS-001, UI-001, A11Y-001, CLIENT-001, SECVAL-001, PROD-001
- rules_failed: none
- evidence_paths: [plan.md](plan.md), [architecture.md](architecture.md)
- delivery_state_updated: yes
