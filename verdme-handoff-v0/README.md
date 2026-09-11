# Verdme · Handoff de referencia v0

**Estado:** referencia de trabajo, no identidad final ni especificación de contratos.

Este paquete permite a Didier preparar una rama de validación visual y conservar el contexto para agentes de IA. El resultado esperado es aplicar la identidad de forma global y contrastarla con el prototipo; no portar ni reutilizar directamente el HTML estático como código de producción.

## Contenido

| Carpeta | Propósito | Uso permitido |
| --- | --- | --- |
| `prototype/` | Snapshot navegable actual de Pacientes, Procesos clínicos y Agenda. | Referencia visual y de densidad. |
| `requirements/` | Instructivo original de entrega técnica. | Fuente de verdad para tema e iconos. |
| `decisions/` | Dirección visual, límites y propuestas UX. | Contexto para diseño e implementación. |
| `theme-draft/` | Inventario de tokens observados y propuesta de normalización. | Punto de partida; requiere validación antes de activar. |

## Orden de trabajo recomendado

1. Crear un tema nuevo de prueba; no reemplazar `verdme-calm`, `verdme-landing` ni `verdme-zen`.
2. Aplicar únicamente tokens globales y una sola familia tipográfica local.
3. Validar primero la ficha de Pacientes como superficie madre de comparación.
4. Aplicar la misma gramática a Procesos y Agenda sin recrear sus flujos.
5. Tratar los cambios de UX de `decisions/ux-proposals.md` como propuestas que requieren revisión técnica previa.
6. Integrar la iconografía solo cuando exista el set completo de 109 SVG validables.

## Regla principal para agentes de IA

No interpretar los mocks como cambios ya aprobados de API, base de datos o navegación real. Si una decisión requiere crear asociaciones, filtros persistentes, nuevas rutas, consultas o migraciones, debe detenerse y validarse con producto y arquitectura.

## Qué queda deliberadamente pendiente

- Fuente WOFF2 local y `README-license.md`.
- `theme-delivery.json` definitivo y contraste medido.
- Set completo de iconos SVG.
- Estados, vistas móviles, login y notas solicitados en el brief.
- Aprobación técnica de los cambios UX.

Ver `requirements/identity-brief-from-didier.md` para el contrato técnico completo.
