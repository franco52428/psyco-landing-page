# Snapshot del prototipo

Este directorio es una copia exacta del prototipo web en el momento del handoff.

## Cómo usarlo

- Abrir `index.html` en un navegador para revisar Pacientes, Procesos clínicos y Agenda.
- Mantener juntos `index.html`, `avatars/`, `brand/`, `art/` y `process-assets/`; el HTML usa rutas relativas.
- Los datos, filtros y navegación son **mock**. Son útiles para evaluar la experiencia, no para inferir contratos de API.

## Invariantes visuales aprobadas hasta ahora

1. Una sola familia tipográfica: Bricolage Grotesque.
2. Pacientes usa hojas botánicas sin contenedor rectangular.
3. Procesos usa un dossier/señal más estructurado, no hojas de paciente.
4. Pacientes es la referencia de densidad y jerarquía para desplegables.
5. Agenda ofrece Lista y Calendario como dos visualizaciones de las mismas sesiones.

## No reutilizar directamente

- PNGs de hojas/dossier como iconos de sistema.
- Caracteres Unicode del mock como reemplazo de los iconos de producción.
- CSS por pantalla del prototipo como arquitectura del tema real.
