# Propuestas UX — no implementar sin revisión técnica

## Pacientes

La ficha se reorganiza alrededor de tres bloques colapsados:

1. **Información personal**: contacto, documentos, consentimiento y datos personalizados.
2. **Información clínica**: procesos vinculados; el detalle vive en Procesos clínicos.
3. **Resumen financiero**: consolidado del paciente y enlace a Cobros filtrado.

No se priorizan alarmas, acciones pendientes ni tarjetas superiores. El encabezado conserva solo información estable del paciente.

## Procesos clínicos

El proceso es el contenedor operativo de la atención. La propuesta de ficha incluye:

- Contexto del proceso.
- Notas del proceso.
- Estado clínico.
- Planes terapéuticos.
- Sesiones.
- Enlace a cobros filtrados.

### Decisión deseada

Desde un proceso, crear una sesión o nota debería asociarla silenciosamente a ese proceso. El psicólogo no debería repetir esa asociación.

### Pendiente técnico

Confirmar la relación persistente de las notas con `clinicalProcessId` y las validaciones necesarias para sesión, participante y proceso.

## Agenda

La Agenda tiene dos vistas del mismo universo de sesiones:

- **Sesiones**: lista agrupada por día, con filtros de paciente, proceso y rango.
- **Calendario**: semana con selector de fecha; no duplica filtros.

Al entrar desde un proceso a “Ver sesiones”, Agenda debería llegar con el proceso aplicado como filtro visible y removible. En procesos con varios participantes, el proceso es la llave principal; no se debe asumir un filtro de paciente con AND que pueda ocultar sesiones válidas.

## Regla de decisión

Si una propuesta solo cambia estilo, tipografía, iconos o presentación de información existente, puede tratarse como UI. Si cambia la navegación, dónde se crea algo, qué se asocia o qué datos se consultan, debe estimarse como UX + revisión de arquitectura.
