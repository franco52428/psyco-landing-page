# Inventario de tokens observado en el prototipo

**Estado:** propuesta de normalización. No es todavía `theme-delivery.json` ni debe activarse sin completar fuente local, licencia y contraste.

| Rol semántico | Valor de referencia | Observación |
| --- | --- | --- |
| Fondo de aplicación | `#F6F6F3` | Cálido muy claro. |
| Superficie | `#FFFFFF` | Paneles y lectura. |
| Texto principal | `#242926` | Nunca negro puro. |
| Texto secundario | `#6C746E` | Metadatos y ayuda. |
| Verde principal | `#315B43` | Acción, selección y señal. |
| Verde profundo | `#263C2E` | Acción primaria oscura. |
| Selección suave | `#E2E7E0` | Listas y navegación activa. |
| Fondo de evento | `#E2F0E5` | Sesiones del calendario. |
| Línea suave | `#DFE4DE` | Divisores principales. |
| Línea de control | `#D8DCD7` | Bordes de inputs y controles. |

## Tipografía candidata

- **Familia:** Bricolage Grotesque.
- **Pesos vistos:** 400, 500 y 600.
- **Estado de entrega:** el prototipo usa una carga remota. Para integrar en Psyco se debe incluir WOFF2 local y `README-license.md`.

## Próximo cierre

1. Definir identificador definitivo del tema, por ejemplo `verdme-forest`.
2. Validar cada par de contraste requerido por el brief.
3. Consolidar valores finales en el esquema completo de `theme-delivery.json`.
4. Conservar `replaceExistingTheme: null` hasta aprobación explícita de reemplazo.
