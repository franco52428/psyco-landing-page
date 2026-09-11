# Límites de implementación

## Sí puede avanzar en la rama de validación visual

- Registro de un tema adicional con tokens globales.
- Fuente local global una vez se entregue su archivo y licencia.
- Sustitución global de iconos al recibir el catálogo completo validado.
- Ajustes de color, tipografía, bordes, radios, sombras, espaciado y estados de componentes existentes.
- Comparación visual contra el snapshot incluido.

## No debe hacerse por inferencia desde este paquete

- Cambiar contratos de API, entidades, queries, índices o migraciones.
- Crear nuevas asociaciones persistentes entre sesiones, notas, pacientes y procesos.
- Reemplazar rutas o flujos de creación existentes.
- Eliminar campos, acciones o pantallas de producción porque no aparezcan en un mock.
- Convertir un prototipo HTML en componentes de producción mediante copia literal.

## Puntos que requieren revisión técnica

| Propuesta | Riesgo técnico potencial |
| --- | --- |
| Crear notas desde un proceso y asociarlas silenciosamente | Hoy debe validarse el modelo de notas y su relación con proceso/sesión. |
| Crear sesiones desde un proceso con proceso fijo | Requiere definir qué campos quedan editables y validar participantes. |
| Abrir Agenda filtrada desde un proceso | Debe cablearse a filtros/query params reales y definir el retorno. |
| Agenda creada desde la sección general | El proceso es la llave; sus pacientes deberían mostrarse como información, no editarse por defecto. |
| Cobros abiertos desde Paciente o Proceso | Requiere filtros persistentes en Cobros, no nuevos resúmenes inventados. |

## Referencia visual madre

La ficha de **Pacientes** ya aprobada es la superficie contra la cual se debe validar:

- jerarquía tipográfica;
- uso de blanco, verde suave y líneas finas;
- separación de secciones;
- densidad y comportamiento de desplegables.
