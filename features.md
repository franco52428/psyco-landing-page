# Funcionalidades verificadas de Verdme

Este documento es la fuente de verdad comercial para la landing page. Su objetivo es evitar que la comunicación prometa capacidades que el producto todavía no ofrece.

## Cuenta de práctica independiente

El formulario de registro del portal permite crear una cuenta personal, activar la invitación y configurar el segundo factor. La práctica accede a los módulos de Basic cuando se activa la suscripción. La oferta que muestra el portal determina el primer cobro y el período de prueba aplicable. El enlace «Crear cuenta» dirige a `/signup`. La verificación de esta entrega se realizó en local con Mercado Pago TEST.

## Fuente y alcance de la auditoría

- Repositorio auditado: `psyco-web`.
- Rama auditada: `origin/main`.
- Commit auditado: `5c76c04` (`fix(finances): aclarar movimientos y cuentas por cobrar del mes (#62)`).
- Fecha de revisión: 2026-09-10.
- Alcance: interfaz, contratos de servicios, rutas autenticadas, textos de producto y pruebas presentes en `psyco-web`.
- Límite: esta revisión no certifica infraestructura, regulación, SLA, disponibilidad de terceros ni capacidades que existan solo en otros repositorios.
- Revisión puntual de procesos con varios participantes y su vista Pacientes: `psyco-web/main`, commit `ec4413f`, 2026-10-25. Evidencia: `components/clinical-process-detail/participants-card/participants-card.tsx` y `lib/services/clinical-process-detail.ts`. Confirma la asociación y presentación de varios pacientes en un mismo proceso clínico.

Cada cambio de mensaje comercial debe contrastarse con este archivo y, cuando sea necesario, volver a validarse contra el `main` vigente de `psyco-web`.

## Auditoría de coherencia editorial — 2026-11-24

- La revisión completa del copy de `index.html` unifica la audiencia como psicólogos independientes y centros de atención psicológica; usa “pacientes” y “sesiones” de forma consistente fuera del checkout aprobado.
- La denominación “centro de atención psicológica” está respaldada por el uso público de la [Universidad de los Andes](https://cienciassociales.uniandes.edu.co/centro-de-atencion-psicologica/quienes-somos/) y la [UPB](https://upb.edu.co/centro-de-atecion-psicologica-medellin), consultadas el 2026-11-24. No es una forma jurídica ni un sinónimo de IPS: esas fuentes describen figuras de prestación diferentes. El término identifica la actividad; “equipo” describe la operación compartida.
- Cambios de claridad: Procesos clínicos abarca atención individual, de pareja, familiar y grupal; Pacientes describe datos, consentimientos y procesos; Finanzas diferencia lo registrado y lo pendiente; Pagos online describe enlaces y actualización de estados; Atención en equipo explica agenda y accesos según función.
- Se elimina del cierre la afirmación absoluta “Lo demás ya está en su lugar”. Se conserva la invitación a asesoría con un mensaje aplicable tanto a práctica independiente como a equipos.
- No se modifican capacidades, interfaces de producto, checkout Wompi, precio, ocho prestaciones ni condiciones de Basic. El precio de Equipos continúa sujeto a cotización y los enlaces de condiciones bajo las tarjetas se identifican como los de Basic.

## Capacidades disponibles y promocionables

### Psicólogos independientes y centros de atención psicológica

- Verdme contempla espacios de trabajo independientes y de organización.
- Las organizaciones reúnen profesionales vinculados y permiten administrar usuarios, roles y permisos, según los accesos habilitados.
- La vista de pacientes de la organización permite buscar por nombre o documento y registrar pacientes con los permisos correspondientes. Su alcance administrativo no equivale a abrir la historia clínica.
- Los usuarios autorizados pueden activar o desactivar profesionales vinculados y consultar las licencias contratadas, en uso y disponibles; la activación requiere capacidad disponible y la desactivación libera una licencia.
- Los roles personalizables permiten separar las tareas de agenda y cobros del acceso clínico; por ejemplo, configurar recepción para agendar y registrar pagos sin habilitar la historia clínica. Es una posibilidad de configuración, no un rol predeterminado ni acceso clínico denegado para todos los miembros.
- La agenda transversal permite coordinar las citas de los profesionales vinculados. La gestión de cobros y el registro de pagos de esas citas se habilitan mediante permisos específicos; “gestión centralizada de pagos” describe esas operaciones, sin afirmar que Verdme reciba o custodie fondos.
- La landing se dirige a psicólogos independientes y centros de atención psicológica: equipos que prestan atención bajo una misma razón social, según la definición de audiencia confirmada por el responsable del producto el 2026-11-24.
- “Centros de atención psicológica” es una denominación comercial de la audiencia; no afirma una categoría de habilitación sanitaria ni permite inferir tarifas o condiciones específicas para organizaciones.

Verificación puntual: `psyco-web/main`, commit `9fc8fcb37c8d9f66051347724c7d9c2e29be633c`, 2026-11-24. Evidencia:

- `components/workspace/workspace-selector.tsx` (espacios independientes y de organización).
- `components/organization-management/organization-management-copy.ts` (profesionales vinculados, usuarios, roles y permisos).
- `lib/services/organization-management.ts` (consulta de miembros y gestión de roles y asignaciones).
- `components/cross-professional-agenda/cross-professional-agenda-page.tsx` y `components/cross-professional-agenda/cross-agenda-sessions.tsx` (agenda del equipo).
- `components/finances/cross-professional-session-billing.test.tsx` y `components/organization-management/role-permission-concepts.ts` (permisos de cobros y pagos de otros profesionales).
- `components/organization-patients/organization-patients-page.tsx`, `components/organization-patients/organization-patient-directory-source.ts` y `lib/services/organization-patients.ts` (búsqueda y registro de pacientes, con información general y permisos separados).
- `components/organization-management/organization-members-panel.tsx` y `components/organization-management/organization-management-copy.ts` (activación, desactivación y capacidad de licencias).

Mensaje vigente para la sección de centros, ajustado el 2026-11-24 a petición del responsable del producto para mantener el tono de la landing: “La gestión de tu equipo, en un mismo lugar.”. La auditoría editorial sustituye “Coordina tu centro” por un beneficio operativo concreto y usa “centros de atención psicológica” para la audiencia. Sus cuatro bloques presentan agenda del equipo, accesos según cada función, pacientes y pagos, y usuarios y licencias. No agrega capacidades: conserva las operaciones verificadas y el ejemplo de recepción con permisos administrativos separados de la historia clínica.

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

### Captura de datos para RDA de Paciente y Consulta Externa

El responsable del producto confirmó el 2026-11-24 que Verdme ya soporta datos de RDA del paciente y de consulta externa. La revisión de `psyco-web/main` (`9fc8fcb37c8d9f66051347724c7d9c2e29be633c`) verifica la captura de información en las fichas y sesiones:

- Identificación del paciente, documento, nombres, nacimiento, contacto, residencia, información demográfica y datos de aseguramiento, con catálogos y campos marcados para RDA en la interfaz.
- Antecedentes de problemas de salud, medicamentos y antecedentes familiares, con estado de información y detalles.
- Datos clínicos por paciente dentro de la sesión: diagnósticos, alergias e intolerancias, factores de riesgo, incapacidades, formulación y órdenes, según funciones y permisos habilitados.
- Guardado progresivo de información; los indicadores RDA de los formularios no obligan a completar todos los datos para guardar un registro.
- Los registros clínicos estructurados tienen historial de revisiones; los permisos de consulta y edición se aplican por bloque.

Evidencia adicional a las tarjetas de sesión: `components/patient-detail/patient-demographic-fields.tsx`, `patient-general-information-card.tsx`, `patient-antecedent-card.tsx`, `patient-antecedents-copy.ts`, `lib/services/patient-detail.ts`, `lib/services/patient-antecedents.ts`, `lib/i18n.ts` (indicación de campos RDA de Paciente), `lib/prescribed-medication-translations.ts` y `lib/service-request-translations.ts` (indicación de captura de datos para RDA de Consulta Externa).

La [descripción oficial de Minsalud](https://www.minsalud.gov.co/ihce/rda/Paginas/inicio.aspx), consultada el 2026-11-24, identifica RDA de Paciente y de Consulta Externa y el nombre Resumen Digital de Atención. Esta fuente fundamenta la denominación, no certifica capacidades de Verdme. La landing comunica **registro de datos para RDA**, sin prometer cobertura exhaustiva de todos los requisitos del perfil, documentos RDA generados/validados/firmados, envío a Minsalud, aceptación en IHCE, integración operativa ni certificación de cumplimiento. El plan de interoperabilidad del repositorio sigue separando esas etapas; no usarlo como prueba de que ya estén disponibles.

### Detalle de la atención y ficha clínica por sesión

Verificación puntual de `psyco-web/main`, commit `9fc8fcb37c8d9f66051347724c7d9c2e29be633c`, 2026-11-24. La landing anterior solo describía agenda y notas; el producto también dispone de captura clínica estructurada.

- La vista “Detalle de la atención” reúne notas y ficha clínica por paciente dentro de la sesión. La navegación separa los participantes y ofrece la nota general cuando corresponde.
- Diagnósticos con descripción, códigos consultables en catálogos, distinción entre principal y relacionados y tipo de diagnóstico. La aplicación registra la información aportada por el profesional; no realiza diagnósticos automáticos.
- Alergias e intolerancias con descripción, estado clínico, verificación y fecha de inicio cuando se registra.
- Factores de riesgo registrados mediante catálogo o descripción, con estado de información.
- Registro de información sobre incapacidades, con periodo y días cuando se consignan.
- Registro de formulación con medicamentos, dosis, vías, duración e indicaciones cuando se consignan.
- Registro de órdenes de procedimientos u otras tecnologías, con descripción y datos de clasificación cuando se consignan.
- Historial de revisiones para los registros clínicos estructurados. No equivale a un historial de cambios palabra por palabra de todas las notas ni una garantía de inmutabilidad.
- Consulta y edición controladas por permisos específicos para cada bloque; la vista solo muestra los bloques accesibles para el usuario.
- Inicio y finalización de la atención. La acción de finalizar guarda la nota antes de cerrar la sesión; no implica firma electrónica ni envío de RDA.

Evidencia principal:

- `components/sessions/session-clinical-record-view.tsx` y `components/sessions/session-patient-navigation.tsx`.
- `components/notes/clinical-notes-workspace.tsx` y `components/sessions/session-care-controls.tsx`.
- `components/sessions/use-session-clinical-capture-access.ts`.
- `components/diagnoses/session-diagnoses-card.tsx`, `diagnosis-contract.ts`, `diagnosis-code-field.tsx` y sus servicios de catálogo/guardado/historial.
- Los contratos, tarjetas de sesión y servicios de historial de `components/allergy-intolerances/`, `components/risk-factors/`, `components/incapacities/`, `components/prescribed-medications/` y `components/service-requests/`.

Regla comercial: destacar la información organizada por paciente y sesión, las notas y los registros estructurados bajo criterio del profesional. Describir incapacidades, formulación y órdenes como **registro de información**, según funciones habilitadas y alcance de la práctica; no atribuir a todos los psicólogos facultad para prescribir medicamentos o emitir incapacidades, ni prometer expedición de documentos, certificación, interoperabilidad o cumplimiento normativo a partir de estos campos. No afirmar que todas las capacidades nuevas forman parte de Basic sin una confirmación comercial específica. La sección usa una lista explicativa de categorías, no una pantalla ficticia ni datos clínicos de personas.

### Pacientes, procesos clínicos y seguimiento

- Directorio y creación de pacientes.
- Perfil de paciente con datos de contacto, campos personalizados y contactos de emergencia.
- Asociación de pacientes a procesos clínicos.
- Procesos con uno o varios participantes, útil para atención individual, de pareja, familiar o grupal sin prometer una metodología clínica específica.
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

- La vista actual usa navegación lateral con Movimientos del mes, Todo lo que te deben, Sesiones sin valor de cobro y Wompi, según los permisos disponibles. En Movimientos del mes, el selector de mes acompaña al título; las tarjetas de Ingresos, Por cobrar y Sesiones muestran su desglose en listas compactas.
- El directorio de movimientos separa Obligaciones de Pagos y devoluciones, con búsqueda por paciente o proceso, filtros de tipo y estado, y acciones por fila.
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

Verificación puntual del diseño de la vista ilustrativa: `psyco-web/main`, commit `9fc8fcb37c8d9f66051347724c7d9c2e29be633c`, 2026-11-24. Referencias: `components/finances/finances-client-page.tsx`, `components/finances/finances-navigation.module.css`, `components/ui/psyco-summary-metric-card.tsx`, `components/ui/psyco-data-table-card.tsx`, `components/ui/psyco-workspace-navigation-item.module.css`, `app/winter-theme.css` y `app/globals.css`. La demostración de la landing conserva el lienzo completo de escritorio al escalarlo y usa datos ficticios.

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

### Plan y licencia

- Por decisión expresa del responsable del producto del 2026-11-24, la sección comercial presenta dos opciones: **Basic** para psicólogos independientes y **Equipos**, con cotización **A tu medida** para centros de atención psicológica. Equipos incluye todo lo de Basic para cada psicólogo, gestión centralizada de la agenda, gestión centralizada de cobros y pagos, y permisos personalizados para los usuarios vinculados. Esta aprobación no fija un precio para Equipos ni extiende automáticamente las condiciones de la suscripción Basic a una propuesta de equipo.
- La composición aprobada toma como referencia únicamente el diseño de precios de `index-propuesta-4.html`: dos tarjetas, Basic clara y Equipos oscura, listas con marcas de verificación y acciones de asesoría y cotización. El contenido de esa propuesta no es una fuente independiente de capacidades o condiciones.
- El plan actual es **Basic por $99.000 COP al mes**, según confirmación expresa del responsable del producto el 2026-09-25 y la documentación de suscripciones de `psyco-web` en `main` (`5ba2133`). La app consulta el importe vigente a Mercado Pago y muestra las condiciones antes de autorizar el pago.
- El responsable del producto definió el 2026-09-25 las características que deben listarse en Basic: gestión de pacientes, gestión de agenda, procesos clínicos, historia clínica, cobros online a pacientes, módulo de finanzas, cifrado y seguridad de datos, y acceso al sistema 24/7. Es una lista comercial de prestaciones incluidas, no un recuento de módulos técnicos.
- “Historia clínica” se refiere al expediente clínico unificado, los registros y las notas que organiza el profesional; no a la generación automática de una historia. “Cifrado” se limita a los datos clínicos sensibles verificados arriba. “Acceso al sistema 24/7” describe que la licencia permite usar Verdme a cualquier hora; no equivale a un SLA ni a disponibilidad ininterrumpida garantizada.
- Es una suscripción mensual sin anualidad ni permanencia. No hay cargos ocultos ni penalidad por cancelar, según confirmación del responsable del producto.
- El usuario activa su suscripción y consulta o administra su licencia, pagos, medio de pago y cancelación de forma autónoma desde Verdme. La cancelación está disponible en **Ajustes → Licencia**.
- La cancelación confirmada detiene renovaciones futuras; el acceso continúa hasta terminar el periodo pagado. El periodo pagado no tiene devolución automática y cancelar no elimina pacientes ni datos clínicos.
- Según la política confirmada por el responsable del producto el 2026-09-25, la información permanece disponible para reactivación autónoma durante un año desde la confirmación de la cancelación. Al reactivar dentro de ese plazo, el profesional retoma su información como la dejó. Después de ese año, debe solicitar a soporte la recuperación de la información; este plazo de acceso autónomo no sustituye los deberes legales de conservación aplicables.

Evidencia principal:

- `psyco-web/components/subscriptions/plans-experience.tsx`
- `psyco-web/components/subscriptions/license-management.tsx`
- `psyco-web/lib/i18n.ts` (textos de oferta, licencia y condiciones legales)
- `psyco-web/app/plans/page.tsx`
- `psyco-web/documentation/features/saas-subscriptions-entitlements/release-checklist.md`
- `psyco-api/src/subscription-billing/services/subscription-catalog.service.ts` (nombres de los siete módulos)

Regla comercial: mostrar $99.000 COP/mes para Basic y comunicar su activación y cancelación autónomas, sin permanencia, penalidad por cancelar, trabas ni costos ocultos. Presentar su lista de características confirmada arriba, sin llamarlas a todas módulos. Equipos se presenta como A tu medida y dirige a cotizar con un asesor, sin inventar tarifas ni condiciones de contratación. No presentar otras ofertas, descuentos, prueba gratuita ni anualidad. Explicar la cancelación y el periodo pagado de Basic sin insinuar una devolución automática.

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
- prueba gratuita, otros precios, SLA o condiciones comerciales no documentadas.

## Reglas de actualización

1. Toda frase nueva de la landing debe poder mapearse a una capacidad de este documento.
2. Si una capacidad cambia en `psyco-web`, actualizar primero `features.md` con el commit auditado y después la landing.
3. Las mejoras futuras o ramas de trabajo no se presentan como disponibles hasta que estén integradas en `main`.
4. Separar siempre capacidad de beneficio: la capacidad debe ser literal y verificable; el beneficio puede ser aspiracional, pero nunca garantiza resultados clínicos, financieros o legales.
5. Los mockups pueden usar datos ficticios únicamente para ilustrar funciones existentes y deben evitar métricas, testimonios o resultados no comprobados.
