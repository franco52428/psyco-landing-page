# Funcionalidades verificadas de Verdme

Este documento es la fuente de verdad comercial para la landing page. Su objetivo es evitar que la comunicación prometa capacidades que el producto todavía no ofrece.

## Fuente y alcance de la auditoría

- Repositorio auditado: `psyco-web`.
- Rama auditada: `origin/main`.
- Commit auditado: `5c76c04` (`fix(finances): aclarar movimientos y cuentas por cobrar del mes (#62)`).
- Fecha de revisión: 2026-09-10.
- Alcance: interfaz, contratos de servicios, rutas autenticadas, textos de producto y pruebas presentes en `psyco-web`.
- Límite: esta revisión no certifica infraestructura, regulación, SLA, disponibilidad de terceros ni capacidades que existan solo en otros repositorios.

Cada cambio de mensaje comercial debe contrastarse con este archivo y, cuando sea necesario, volver a validarse contra el `main` vigente de `psyco-web`.

## Capacidades disponibles y promocionables

### Agenda y sesiones

- Vista de agenda y calendario.
- Creación, edición y eliminación de sesiones.
- Sesiones asociadas a un proceso clínico y a uno o varios participantes.
- Registro de hora de inicio y finalización.
- Consulta del detalle de una sesión.
- Registro de inasistencia cobrable.
- Decisión de cobro por sesión: independiente, incluida en paquete o sin cobro.
- Señales de sesión documentada y presencia de nota clínica.

Evidencia principal en `psyco-web`:

- `app/(authenticated)/(agenda)/sessions/page.tsx`
- `app/sessions/agenda-workspace.tsx`
- `components/sessions/calendar.tsx`
- `components/sessions/editor.tsx`
- `components/sessions/session-detail-view.tsx`
- `lib/services/sessions.ts`

### Pacientes, procesos clínicos y seguimiento

- Directorio y creación de pacientes.
- Perfil de paciente con datos de contacto, campos personalizados y contactos de emergencia.
- Asociación de pacientes a procesos clínicos.
- Procesos con uno o varios participantes, útil para atención individual, de pareja o familiar sin prometer una metodología clínica específica.
- Estados de proceso: activo, pausado y cerrado.
- Motivo de consulta, fecha de inicio y línea de tiempo del proceso.
- Estado clínico con hipótesis actual, diagnóstico, objetivos activos, estado emocional y riesgos.
- Planes terapéuticos con objetivos, intervenciones planeadas e indicadores de progreso; se pueden crear, editar y archivar.
- Historial de sesiones y estados dentro del proceso.
- Panel con procesos recientes, pausados o sin próxima sesión.

Evidencia principal:

- `app/(authenticated)/patients/**`
- `app/(authenticated)/clinical-processes/**`
- `components/patient-detail/**`
- `components/clinical-process-detail/**`
- `lib/services/patient-detail.ts`
- `lib/services/clinical-processes.ts`
- `lib/services/clinical-process-detail.ts`

### Notas clínicas y documentación

- Notas asociables a una sesión, a un paciente o a ambos contextos.
- Editor de texto enriquecido con formato, listas, enlaces y citas.
- Dictado por voz que inserta texto en el editor cuando el navegador lo soporta.
- Lectura en voz alta del contenido mediante las capacidades de voz del navegador.
- Subrayado, resaltado y trazos/dibujos sobre el contenido de la nota.
- Adjuntos protegidos en PDF, Word, texto e imágenes compatibles, con límite de 10 MB por archivo en la interfaz auditada.
- Historial de notas por paciente, con filtros por contexto, adjuntos y rango de fechas.
- Creación, edición, cambio de contexto y eliminación de notas.

Evidencia principal:

- `components/ui/psyco-rich-text-editor.tsx`
- `components/voice-dictation/**`
- `components/text-to-speech/**`
- `components/notes/**`
- `lib/services/clinical-notes.ts`

Regla comercial: describir el dictado como una forma de escribir o capturar notas con la voz. No decir que la aplicación interpreta la sesión, redacta historias clínicas, resume, diagnostica o genera documentación mediante inteligencia artificial.

### Consentimientos

- Registro de consentimientos mediante carga de archivo.
- Asociación del consentimiento a uno o varios procesos clínicos del paciente.
- Registro de fecha de firma, vigencia y región (`LATAM`, `US`, `EU`).
- Estados visibles de consentimiento: pendiente, vigente o vencido.
- Consulta de historial y descarga protegida del documento.
- Panel de consentimientos pendientes.

Evidencia principal:

- `app/(authenticated)/patients/[patientId]/consents/new/page.tsx`
- `components/consent/**`
- `components/dashboard/pending-consents-card/**`
- `lib/services/consents.ts`

Regla comercial: Verdme registra y organiza consentimientos. No afirmar que los persigue, solicita, firma electrónicamente, valida jurídicamente ni garantiza cumplimiento normativo si esas capacidades no se verifican de nuevo.

### Finanzas, cobros y paquetes

- Resumen mensual de ingresos registrados, cuentas por cobrar y actividad de sesiones y paquetes.
- Filtros de movimientos, cuentas por cobrar y pendientes de definición.
- Acuerdos de cobro por proceso clínico.
- Registro manual de pagos y su medio: efectivo, transferencia, billetera, terminal externo u otro.
- Evidencia opcional de pagos manuales.
- Registro de devoluciones, revisiones y correcciones conservando trazabilidad.
- Paquetes de sesiones con nombre, cantidad de sesiones y valor total.
- Activación, edición, desactivación y traslado de paquetes entre procesos según las reglas del producto.
- Asociación de sesiones a paquetes y control separado de uso de sesiones y dinero recibido.
- Planes de pago por cuotas con valor y fecha límite; seguimiento de próxima cuota, saldo y vencimiento.
- Vista de pagos vencidos y próximos cobros.

Evidencia principal:

- `app/(authenticated)/finances/**`
- `components/finances/**`
- `lib/services/finances.ts`
- `lib/services/finance-contracts.ts`
- `lib/i18n.ts` en las claves `finances_*`.

### Integración con Wompi

- Conexión de una cuenta Wompi propia del profesional mediante credenciales de integración.
- Configuración de URL de Eventos para seguimiento de transacciones.
- Creación de cuentas de cobro para sesiones o paquetes.
- Generación de links de pago con monto, fecha de vencimiento y segmentación opcional de impuestos.
- Para paquetes con plan de pago, sugerencia de la próxima cuota y su saldo pendiente.
- Copia del link y apertura de WhatsApp con el link listo para compartir; el envío final lo hace el usuario.
- Consulta y actualización del estado reportado por Wompi.
- Registro de identificador de transacción, estados, pagos, reversiones y trazabilidad relacionada.
- El pago se procesa en la cuenta Wompi del profesional. Verdme facilita la integración y no recibe ni custodia el dinero.

Evidencia principal:

- `app/(authenticated)/finances/wompi/page.tsx`
- `components/finances/wompi-connection-settings-page.tsx`
- `components/finances/finance-payment-link-modal.tsx`
- `components/finances/finance-payment-detail-content.tsx`
- `lib/services/finances.ts`
- `lib/i18n.ts` en las claves `finances_connection_*` y `finances_link_*`.

Reglas comerciales:

- Hablar de “cuenta de cobro” o “link de cobro”, no de factura electrónica.
- Decir “compartir por WhatsApp”, no “Verdme envía automáticamente por WhatsApp”.
- Los medios de pago del checkout pertenecen a Wompi y pueden depender de la configuración o disponibilidad del comercio.
- No insinuar que Verdme recibe, administra o retiene fondos.

### Acceso y seguridad visibles en el producto

- Opciones de acceso mediante passkey, contraseña y TOTP según la configuración habilitada para la cuenta.
- Recuperación de acceso y configuración de métodos de seguridad.
- Centro de sesiones con dispositivo, navegador, ubicación aproximada, última actividad y nivel de riesgo informado por el servicio.
- Cierre de sesiones activas y reporte de una sesión como sospechosa.
- Historial de sesiones de seguridad.
- El backend cifra notas clínicas, detalles sensibles de pacientes y archivos almacenados. Esta afirmación se limita a esos datos; no implica que todos los datos de la aplicación estén cifrados ni una garantía de disponibilidad.

Evidencia principal:

- `app/login/**`
- `app/registration/**`
- `app/settings/security/**`
- `app/security/security-center-client-page.tsx`
- `lib/services/security.ts`
- Auditoría puntual de `psyco-api` en `main` (`b978825`): `src/crypto/crypto.service.ts`, `src/clinical-notes/clinical-note.repository.ts`, `src/patients/patient-detail.repository.ts`, `src/file-storage/file-crypto.service.ts` y `src/file-storage/file-storage.service.ts`.

Regla comercial: hablar de control de acceso, visibilidad de sesiones y cifrado solo para los datos sensibles verificados arriba. No prometer certificaciones, cumplimiento regulatorio, cifrado total de historias clínicas, respaldos 24/7, disponibilidad garantizada o “seguridad de grado corporativo” sin evidencia específica y vigente.

### Experiencia transversal

- Diseño adaptable a escritorio y móvil.
- Aplicación web instalable mediante manifiesto PWA en navegadores compatibles.
- Interfaz disponible en español, inglés, portugués y francés.
- Dashboard con agenda del día, procesos recientes, procesos sin próxima sesión, notas recientes y consentimientos pendientes.

Evidencia principal:

- `app/manifest.ts`
- `docs/pwa-installation.md`
- `lib/i18n.ts`
- `components/dashboard/**`

## Capacidades no verificadas: no promocionar

No se encontraron en `origin/main` del frontend auditado pruebas suficientes para afirmar que Verdme ofrece actualmente:

- generación de notas, historias clínicas o resúmenes con inteligencia artificial;
- interpretación automática de lo dicho durante una sesión;
- diagnósticos, sugerencias terapéuticas o recursos psicológicos generados automáticamente;
- alertas clínicas predictivas o priorización automática de riesgos;
- firma electrónica o envío automático de consentimientos;
- recordatorios automáticos de citas o cobros por WhatsApp, SMS o correo;
- videollamadas o teleconsulta;
- facturación electrónica o integración tributaria;
- conciliación bancaria ajena a los registros manuales y a la información reportada por Wompi;
- certificaciones de seguridad o cumplimiento normativo específicas;
- cifrado generalizado fuera del alcance específico verificado arriba, o copias de seguridad con alcances o frecuencias que puedan prometerse públicamente;
- prueba gratuita, precio, permanencia, SLA o condiciones comerciales no documentadas.

## Reglas de actualización

1. Toda frase nueva de la landing debe poder mapearse a una capacidad de este documento.
2. Si una capacidad cambia en `psyco-web`, actualizar primero `features.md` con el commit auditado y después la landing.
3. Las mejoras futuras o ramas de trabajo no se presentan como disponibles hasta que estén integradas en `main`.
4. Separar siempre capacidad de beneficio: la capacidad debe ser literal y verificable; el beneficio puede ser aspiracional, pero nunca garantiza resultados clínicos, financieros o legales.
5. Los mockups pueden usar datos ficticios únicamente para ilustrar funciones existentes y deben evitar métricas, testimonios o resultados no comprobados.
