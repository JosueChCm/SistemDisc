# Requirements Document

## Introduction

El Sistema de Gestión de Ajustes Razonables para Estudiantes con Discapacidad es una aplicación web interna destinada a la Oficina de Bienestar Universitario de una universidad pública. Su propósito es centralizar el registro y el seguimiento de las solicitudes de ajuste razonable que hoy llegan por correo, WhatsApp o en papel y se pierden, dificultan conocer el estado de cada solicitud, dificultan informar al docente el ajuste que corresponde a cada estudiante y dificultan generar el reporte semestral exigido por la Ley N.° 29973 y la Ley Universitaria N.° 30220.

El Sistema permite registrar al Estudiante con su Tipo de Discapacidad y su Documento Acreditador, validar su Número CONADIS, registrar Solicitudes por Asignatura, cambiar el Estado de cada Solicitud, listar lo pendiente por Estudiante y por Asignatura, avisar por correo al Docente cuando una Solicitud es aprobada y obtener el total de Solicitudes por Tipo de Ajuste y por Estado para el Reporte Semestral. El Sistema no evalúa la pertinencia médica del ajuste ni sustituye la decisión de la Oficina. Los propios Estudiantes con discapacidad visual usan el Formulario de Solicitud.

## Formato de los requisitos

- Los requisitos funcionales se identifican **RF1…RF51** y los no funcionales **RNF1…RNF11**.
- Cada requisito es una sola oración en formato EARS: «CUANDO <evento y condiciones>, EL SISTEMA DEBERÁ <respuesta>».
- Los datos entre comillas son los datos de ejemplo simulados de la sección «Datos de ejemplo».
- La columna «Origen» indica la historia del D0 (H1 a H6), la tabla de actores o el supuesto o restricción de la que sale cada requisito.

## Decisiones adoptadas por el equipo (pendientes de confirmación)

El D0 deja cinco puntos abiertos. Para avanzar se adoptó lo siguiente; cada decisión es reversible.

| # | Tema | Decisión adoptada | Requisitos afectados |
|---|---|---|---|
| DA1 | El D0 incluye en el alcance y a la vez excluye: adjuntar el certificado en PDF, validar el Número CONADIS y enviar correo al Docente | **Prevalece el alcance** (historias H1 y H3 y lista de funcionalidades). Se excluye lo que va más allá: otros adjuntos, sincronización con CONADIS y otras notificaciones | RF6–RF12, RF23–RF25 |
| DA2 | Quién cambia el Estado | **Solo la Oficina cambia el Estado.** La decisión del Docente (aprueba o rechaza) se registra aparte y la Oficina la ve. No existe el Estado "rechazada". El correo al aprobar informa al Docente qué ajuste debe aplicar | RF20–RF25, RF38–RF40 |
| DA3 | Qué ve el Docente | Estudiante, Tipo de Ajuste, Estado y su decisión, solo de Solicitudes de sus Asignaturas en Estado evaluada, aprobada o implementada. Nunca datos de discapacidad | RF36, RF37, RNF8 |
| DA4 | Servidor MCP y modelo de lenguaje | **El Sistema no usa servidor MCP ni modelo de lenguaje**: el D0 no los incluye | — |
| DA5 | Creación de cuentas | La Oficina crea la cuenta del Estudiante al registrarlo. Las cuentas de Docentes y de la Oficina y el catálogo de Asignaturas se cargan antes del semestre con un script | RF4, RF5, Supuestos |

## Usuarios y Stakeholders

- **Estudiante**: estudiante con discapacidad (incluidos los de discapacidad visual) que registra Solicitudes mediante el Formulario de Solicitud y consulta su Estado.
- **Oficina de Bienestar Universitario**: registra Estudiantes, registra Solicitudes en nombre de ellos, cambia el Estado, lista lo pendiente y obtiene el Reporte Semestral.
- **Docente**: profesor de la Asignatura a la que corresponde una Solicitud; recibe el aviso de aprobación y registra su decisión.

## Glossary

- **Sistema**: aplicación web interna de Gestión de Ajustes Razonables.
- **Estudiante**: estudiante con discapacidad registrado en el Sistema.
- **Oficina**: Oficina de Bienestar Universitario.
- **Docente**: profesor de la Asignatura a la que corresponde una Solicitud.
- **Asignatura**: curso para el que se solicita un ajuste.
- **Ajuste Razonable**: adaptación solicitada para un Estudiante en una Asignatura.
- **Solicitud**: registro de un Ajuste Razonable de un Tipo de Ajuste para una Asignatura.
- **Tipo de Ajuste**: tiempo adicional en evaluaciones, materiales en formato accesible, intérprete de lengua de señas peruana, aula en primer piso, mobiliario adaptado o acompañamiento en laboratorio. No cambia durante el semestre.
- **Tipo de Discapacidad**: física, visual, auditiva, intelectual u otra que defina la Oficina.
- **Documento Acreditador**: certificado CONADIS o certificado médico en PDF.
- **Número CONADIS**: identificador de 8 dígitos del Estudiante en el registro nacional del CONADIS.
- **Estado de la Solicitud**: recibida, evaluada, observada, aprobada o implementada.
- **Solicitud pendiente**: Solicitud con Estado recibida, evaluada, observada o aprobada (distinto de implementada).
- **Fecha requerida**: fecha desde la cual el Estudiante necesita el ajuste (definición propuesta; el D0 solo habla de "calendario emergente").
- **Formulario de Solicitud**: formulario web con calendario emergente y selección de Asignaturas por arrastrar y soltar.
- **Reporte Semestral**: totales de Solicitudes por Tipo de Ajuste y por Estado de un semestre, con gráfico de barras.

## Datos de ejemplo (simulados)

| Dato | Valor |
|---|---|
| Estudiante E1 | Ana Quispe Huamán · código 2201020099 · correo 2201020099@universidad.edu.pe · visual · Número CONADIS 00123456 |
| Estudiante E2 | Luis Paredes Soto · código 2201020100 · auditiva · Número CONADIS 00123457 |
| Docente D1 | Dra. Rosa Medina · dicta "Matemática I" (MAT101) |
| Docente D2 | Mg. Carlos Rojas · dicta "Física I" (FIS101) |
| Ajustes | A1 "materiales en formato accesible"; A2 "intérprete de lengua de señas peruana" |
| Número inexistente | 99999999 |
| Semestre | 2026-II |

## Alcance

1. Registrar al Estudiante con su Tipo de Discapacidad y crear su cuenta de acceso.
2. Validar el Número CONADIS contra el registro nacional (solo consulta).
3. Adjuntar el Documento Acreditador en PDF.
4. Registrar Solicitudes por Asignatura, por el Estudiante o por la Oficina, mediante el Formulario de Solicitud.
5. Cambiar el Estado de cada Solicitud.
6. Listar las Solicitudes pendientes, por Estudiante y por Asignatura.
7. Avisar por correo al Docente cuando una Solicitud es aprobada.
8. Permitir al Estudiante consultar el Estado de sus Solicitudes y al Docente consultarlas y registrar su decisión.
9. Obtener el Reporte Semestral por Tipo de Ajuste y por Estado.

## Fuera de Alcance

- Archivos adjuntos distintos del Documento Acreditador (informes médicos, etc.).
- Cualquier uso del CONADIS distinto de la consulta para validar el Número (sincronización de datos).
- Notificaciones distintas del correo al Docente al aprobar (incluidos WhatsApp y avisos al Estudiante).
- Integración con el sistema académico de matrícula y con SUNEDU.
- Evaluación médica o calificación de la discapacidad.
- Aplicación móvil nativa.
- Programación de horarios y asignación de aulas.
- Servidor MCP y modelo de lenguaje (DA4).

## Supuestos

- La Oficina cuenta con al menos un responsable que actualiza el Estado de las Solicitudes durante todo el semestre.
- Los Estudiantes y el personal acceden con código o correo institucional.
- Existe acceso técnico al registro nacional del CONADIS para validar el Número (forma de acceso por definir).
- Existe un servidor de correo institucional disponible para el aviso al Docente.
- Los Tipos de Ajuste no cambian durante el semestre.
- Las cuentas de Docentes y de la Oficina y el catálogo de Asignaturas se cargan antes del semestre (DA5).
- La Oficina informa al Estudiante, antes de registrarlo, la finalidad del tratamiento de sus datos (Ley N.° 29733).

## Restricciones

- Uso interno: accesible únicamente desde la red de la universidad.
- Pila tecnológica del D0: Python 3.11+, FastAPI, frontend HTML y JavaScript simple, SQLite, Git y GitHub.
- El Formulario de Solicitud usa calendario emergente y selección de Asignaturas por arrastrar y soltar, con alternativa operable por teclado.
- El Sistema no evalúa la pertinencia médica del ajuste ni sustituye la decisión de la Oficina.
- Las pruebas usan **datos simulados**. El D0 proponía usar datos reales del semestre anterior; se descarta por tratarse de datos sensibles (Ley N.° 29733).

## Requisitos funcionales

### Registro del Estudiante (H1)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF1 | CUANDO la Oficina registre a un Estudiante no registrado con nombre "Ana Quispe Huamán", código "2201020099", correo "2201020099@universidad.edu.pe", Tipo de Discapacidad "visual" y Número CONADIS "00123456", EL SISTEMA DEBERÁ crear el registro del Estudiante. | H1 |
| RF2 | CUANDO la Oficina envíe el registro de un Estudiante sin código institucional, EL SISTEMA DEBERÁ rechazarlo e indicar el campo faltante. | H1 |
| RF3 | CUANDO la Oficina registre a un Estudiante con el código "2201020099" ya registrado, EL SISTEMA DEBERÁ rechazar el registro con el mensaje "Ya existe un Estudiante con ese código." | H1 |
| RF4 | CUANDO el Sistema cree el registro del Estudiante E1, EL SISTEMA DEBERÁ crear su cuenta con el código "2201020099" como identificador y una contraseña temporal aleatoria de 12 caracteres. | H1, DA5 |
| RF5 | CUANDO el Sistema cree la cuenta de un Estudiante, EL SISTEMA DEBERÁ mostrar la contraseña temporal una sola vez a la Oficina. | H1, DA5 |
| RF6 | CUANDO la Oficina registre a un Estudiante con el Número CONADIS "00123456" presente en el registro nacional, EL SISTEMA DEBERÁ marcar el Número CONADIS como verificado. | H1, DA1 |
| RF7 | CUANDO la Oficina registre a un Estudiante con el Número CONADIS "99999999" ausente del registro nacional, EL SISTEMA DEBERÁ rechazar el registro con el mensaje "El Número CONADIS no coincide con el registro nacional." | H1, DA1 |
| RF8 | CUANDO la Oficina registre a un Estudiante y el registro nacional no responda en 10 segundos, EL SISTEMA DEBERÁ rechazar el registro con el mensaje "No se pudo verificar el Número CONADIS; intente más tarde." | H1, DA1 |
| RF9 | CUANDO la Oficina ingrese un Número CONADIS de 7 dígitos, EL SISTEMA DEBERÁ rechazarlo por formato sin consultar el registro nacional. | H1, DA1 |
| RF10 | CUANDO la Oficina adjunte un PDF de 2 MB al Estudiante E1, EL SISTEMA DEBERÁ guardar el Documento Acreditador asociado a E1. | H1, DA1 |
| RF11 | CUANDO la Oficina adjunte al Estudiante E1 un archivo de 6 MB, EL SISTEMA DEBERÁ rechazarlo con el mensaje "Adjunte un archivo PDF de hasta 5 MB." *(límite de 5 MB: propuesta)* | H1, DA1 |
| RF12 | CUANDO la Oficina adjunte al Estudiante E1 un archivo ".docx", EL SISTEMA DEBERÁ rechazarlo con el mensaje "Adjunte un archivo PDF de hasta 5 MB." | H1, DA1 |

### Registro y consulta de Solicitudes (H2)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF13 | CUANDO el Estudiante E1 autenticado envíe el Formulario de Solicitud con Tipo de Ajuste "materiales en formato accesible", Fecha requerida "15/11/2026" y la Asignatura "Matemática I", EL SISTEMA DEBERÁ registrar una Solicitud de E1 con Estado "recibida". | H2 |
| RF14 | CUANDO el Estudiante E1 autenticado envíe el formulario con las Asignaturas "Matemática I" y "Física I", EL SISTEMA DEBERÁ registrar dos Solicitudes, una por Asignatura, ambas con Estado "recibida". | H2 |
| RF15 | CUANDO el Estudiante E1 autenticado envíe el formulario con una Asignatura inexistente, EL SISTEMA NO DEBERÁ registrar ninguna Solicitud. | H2 |
| RF16 | CUANDO el Estudiante E1 autenticado envíe el formulario con el código de otro Estudiante, EL SISTEMA DEBERÁ ignorarlo y registrar la Solicitud a nombre de E1. | H2 |
| RF17 | CUANDO la Oficina registre una Solicitud del Estudiante E2 con Tipo de Ajuste "intérprete de lengua de señas peruana" para "Física I", EL SISTEMA DEBERÁ registrarla con Estado "recibida". | H2, Alcance 4 |
| RF18 | CUANDO la Oficina registre una Solicitud con un código de Estudiante no registrado, EL SISTEMA DEBERÁ rechazarla con el mensaje "Primero debe registrarse al Estudiante." | H2 |
| RF19 | CUANDO la Oficina consulte una Solicitud de E1 para "Matemática I" con Tipo de Ajuste A1 en Estado "recibida", EL SISTEMA DEBERÁ mostrar Estudiante, Asignatura, Tipo de Ajuste, Fecha requerida y Estado. | H2 |

### Cambio de Estado y aviso al Docente (H3)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF20 | CUANDO la Oficina cambie una Solicitud de Estado "recibida" a "evaluada", EL SISTEMA DEBERÁ actualizar el Estado a "evaluada". | H3 |
| RF21 | CUANDO se envíe el Estado "rechazada" para una Solicitud en Estado "recibida", EL SISTEMA DEBERÁ rechazar el valor con el mensaje "Estado no válido." y mantener el Estado "recibida". | H3, DA2 |
| RF22 | CUANDO el Estudiante E1 intente cambiar el Estado de su Solicitud, EL SISTEMA DEBERÁ rechazar la acción con el mensaje "No tiene permiso para esta acción." | H3, DA2 |
| RF23 | CUANDO la Oficina cambie a "aprobada" una Solicitud de E1 para "Matemática I" que está en Estado "evaluada", EL SISTEMA DEBERÁ enviar a la Dra. Rosa Medina, dentro de los 5 minutos siguientes, un correo con el nombre de E1 y el Tipo de Ajuste "materiales en formato accesible". | H3, DA1 |
| RF24 | CUANDO la Oficina seleccione "aprobada" para una Solicitud que ya está en Estado "aprobada", EL SISTEMA NO DEBERÁ enviar otro correo. | H3, DA1 |
| RF25 | CUANDO la Oficina cambie una Solicitud a "aprobada" y el servidor de correo no responda, EL SISTEMA DEBERÁ conservar el Estado "aprobada" y mostrar el aviso "Estado actualizado. No se pudo enviar el correo al Docente." | H3, DA1 |

### Listado de pendientes (H4)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF26 | CUANDO la Oficina abra el listado de pendientes y existan tres Solicitudes en Estado "recibida", "aprobada" e "implementada", EL SISTEMA DEBERÁ mostrar las de Estado "recibida" y "aprobada" y no mostrar la "implementada". | H4 |
| RF27 | CUANDO la Oficina abra el listado de pendientes y no exista ninguna Solicitud pendiente, EL SISTEMA DEBERÁ mostrar el mensaje "No hay solicitudes pendientes." | H4 |
| RF28 | CUANDO la Oficina filtre los pendientes de E1 y E2 por el Estudiante E1, EL SISTEMA DEBERÁ mostrar solo las pendientes de E1. | H4 |
| RF29 | CUANDO la Oficina filtre los pendientes de "Matemática I" y "Física I" por la Asignatura "Física I", EL SISTEMA DEBERÁ mostrar solo las pendientes de "Física I". | H4 |
| RF30 | CUANDO la Oficina filtre por el Estudiante E1 y la Asignatura "Matemática I" a la vez, EL SISTEMA DEBERÁ mostrar solo las pendientes de E1 en "Matemática I". | H4 |

### Reporte Semestral (H5)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF31 | CUANDO la Oficina pida el Reporte Semestral de 2026-II y existan 3 Solicitudes de A1 y 2 de A2 en ese semestre, EL SISTEMA DEBERÁ mostrar en un gráfico de barras 3 para A1 y 2 para A2. | H5 |
| RF32 | CUANDO la Oficina pida el Reporte de 2026-II y exista una Solicitud de A1 de 2026-I, EL SISTEMA NO DEBERÁ contarla. | H5 |
| RF33 | CUANDO la Oficina pida el Reporte de 2026-II y existan 2 Solicitudes "recibida" y 3 "implementada", EL SISTEMA DEBERÁ mostrar 2 para "recibida" y 3 para "implementada". | H5, Alcance 9 |
| RF34 | CUANDO la Oficina pida el Reporte de 2026-II, EL SISTEMA DEBERÁ mostrar una suma de totales por Estado igual a la suma de totales por Tipo de Ajuste. | H5 |

### Estudiante y Docente (tabla de actores del D0)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF35 | CUANDO E1 consulte sus Solicitudes y exista una Solicitud "aprobada" de E1 y una "recibida" de E2, EL SISTEMA DEBERÁ mostrar solo la de E1 con su Estado "aprobada". | Actores |
| RF36 | CUANDO la Dra. Rosa Medina consulte las Solicitudes de "Matemática I" que están en Estados "recibida", "evaluada" y "aprobada", EL SISTEMA DEBERÁ mostrar solo las de Estado "evaluada" y "aprobada", con Estudiante, Tipo de Ajuste y Estado. | Actores, DA3 |
| RF37 | CUANDO la Dra. Rosa Medina consulte sus Solicitudes y exista una Solicitud de "Física I", EL SISTEMA NO DEBERÁ mostrarla. | Actores, DA3 |
| RF38 | CUANDO la Dra. Rosa Medina registre la decisión "rechaza" con el comentario "No hay material en Braille" en una Solicitud de "Matemática I" en Estado "evaluada", EL SISTEMA DEBERÁ guardar la decisión y mostrarla a la Oficina. | Actores, DA2 |
| RF39 | CUANDO el Sistema guarde la decisión "rechaza" de una Solicitud en Estado "evaluada", EL SISTEMA DEBERÁ mantener el Estado en "evaluada". | Actores, DA2 |
| RF40 | CUANDO la Dra. Rosa Medina intente registrar una decisión en una Solicitud de "Física I", EL SISTEMA DEBERÁ rechazar la acción con el mensaje "No tiene permiso para esta acción." | Actores, DA2 |

### Autenticación (supuesto del D0)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF41 | CUANDO E1 inicie sesión con el código "2201020099" y su contraseña correcta, EL SISTEMA DEBERÁ abrir una sesión. | Supuesto |
| RF42 | CUANDO E1 inicie sesión con el correo "2201020099@universidad.edu.pe" y su contraseña correcta, EL SISTEMA DEBERÁ abrir una sesión. | Supuesto |
| RF43 | CUANDO un usuario inicie sesión con una contraseña incorrecta, EL SISTEMA DEBERÁ rechazarlo con el mensaje "Código, correo o contraseña incorrectos." | Supuesto |
| RF44 | CUANDO un usuario con contraseña temporal inicie sesión por primera vez, EL SISTEMA DEBERÁ exigir una contraseña nueva antes de cualquier otra acción. | Supuesto, DA5 |

### Formulario accesible (H6)

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RF45 | CUANDO E1 recorra con NVDA el Formulario de Solicitud, EL SISTEMA DEBERÁ hacer que el lector anuncie, para cada campo (Tipo de Ajuste, Fecha requerida, Asignaturas), su etiqueta y si es obligatorio. | H6 |
| RF46 | CUANDO E1 envíe el formulario sin elegir Tipo de Ajuste, EL SISTEMA DEBERÁ hacer que el lector anuncie "Seleccione un Tipo de Ajuste." y mover el foco a ese campo. | H6 |
| RF47 | CUANDO E1 escriba "15/11/2026" en el campo Fecha requerida, EL SISTEMA DEBERÁ aceptar la fecha sin abrir el calendario. | H6 |
| RF48 | CUANDO E1 pulse la flecha derecha dos veces y Enter con el calendario abierto, EL SISTEMA DEBERÁ seleccionar la fecha dos días posterior a la fecha inicial, cerrar el calendario y devolver el foco al botón "Elegir fecha". | H6 |
| RF49 | CUANDO E1 pulse Escape con el calendario abierto, EL SISTEMA DEBERÁ cerrarlo sin cambiar la fecha. | H6 |
| RF50 | CUANDO E1 pulse Enter sobre "Matemática I" en la lista "Asignaturas disponibles", EL SISTEMA DEBERÁ moverla a "Asignaturas seleccionadas" y hacer que el lector anuncie "Matemática I agregada a seleccionadas, 1 seleccionada". | H6 |
| RF51 | CUANDO E1 envíe un formulario completo, EL SISTEMA DEBERÁ hacer que el lector anuncie "Solicitud registrada." sin que E1 tenga que buscar el mensaje. | H6 |

## Requisitos no funcionales

| ID | Requisito (EARS) | Origen |
|---|---|---|
| RNF1 | **Accesibilidad.** CUANDO se ejecute axe-core sobre cualquier página del Sistema, EL SISTEMA DEBERÁ mostrar 0 infracciones de nivel A y AA de WCAG 2.1. | H6, restricción de accesibilidad |
| RNF2 | **Accesibilidad (teclado).** CUANDO un usuario complete el flujo principal de cualquier página usando solo Tab, Mayús+Tab, flechas, Enter, Espacio y Escape, EL SISTEMA DEBERÁ permitir completarlo, con foco visible de contorno mínimo de 3 px y en el mismo orden que el visual. | H6 |
| RNF3 | **Accesibilidad (lectores de pantalla).** CUANDO se pruebe el Formulario de Solicitud con NVDA y con JAWS, EL SISTEMA DEBERÁ cumplir RF45 a RF51 en ambos. | H6 |
| RNF4 | **Rendimiento.** CUANDO se cargue cualquier página desde la red de la universidad con 500 Estudiantes y 3000 Solicitudes en la base, EL SISTEMA DEBERÁ cargar el 95 % de las páginas en menos de 2 segundos. *(cifras propuestas)* | D0 ("rápido") |
| RNF5 | **Seguridad en tránsito.** CUANDO un cliente proponga una conexión con TLS 1.1, EL SISTEMA DEBERÁ rechazarla y aceptar solo TLS 1.2 o superior. | D0 ("seguro") |
| RNF6 | **Seguridad en almacenamiento.** CUANDO se inspeccione la base de datos y la carpeta de documentos tras registrar a E1, EL SISTEMA DEBERÁ mantener el Número CONADIS, el Tipo de Discapacidad y el Documento Acreditador sin aparecer en texto plano. | D0 ("encriptación") |
| RNF7 | **Protección de datos personales (Ley N.° 29733).** CUANDO un usuario que no sea de la Oficina ni el propio Estudiante solicite los datos de discapacidad de E1, EL SISTEMA DEBERÁ rechazar la solicitud y no revelarlos, conforme a la Ley N.° 29733 de Protección de Datos Personales. | D0 (datos de estudiantes), Ley N.° 29733 |
| RNF8 | **Protección de datos personales (Docente).** CUANDO el Sistema responda a un Docente, EL SISTEMA NO DEBERÁ incluir Tipo de Discapacidad, Número CONADIS ni Documento Acreditador, conforme a la Ley N.° 29733. | DA3, Ley N.° 29733 |
| RNF9 | **Protección de datos personales (datos de prueba).** CUANDO se cargue la base del entorno de pruebas, EL SISTEMA DEBERÁ usar solo Estudiantes del script de datos simulados y ningún dato real, conforme a la Ley N.° 29733. | Restricción del D0, Ley N.° 29733 |
| RNF10 | **Protección de datos personales (registros).** CUANDO se revise el archivo de registros después de registrar a E1, EL SISTEMA NO DEBERÁ contener "00123456" ni "visual", conforme a la Ley N.° 29733. | Ley N.° 29733 |
| RNF11 | **Claves.** CUANDO se busque en el repositorio la clave de cifrado, el secreto de sesión o las credenciales de correo y de CONADIS, EL SISTEMA NO DEBERÁ tenerlas en el código; las leerá de variables de entorno. | Buenas prácticas |

## Matriz de trazabilidad

| Origen en el D0 | Requisitos |
|---|---|
| H1 Registrar al estudiante | RF1–RF12 |
| H2 Registrar solicitud | RF13–RF19 |
| H3 Cambiar estado y avisar al docente | RF20–RF25 |
| H4 Pendientes | RF26–RF30 |
| H5 Totales por tipo de ajuste | RF31–RF34 |
| H6 Formulario compatible con lector de pantalla | RF45–RF51, RNF1, RNF2, RNF3 |
| Tabla de actores (Estudiante, Docente) | RF35–RF40 |
| Supuestos (acceso institucional) | RF41–RF44 |
| RNF del D0 ("rápido", "seguro") | RNF4, RNF5, RNF6 |
| Restricción de datos reales y Ley N.° 29733 | RNF7–RNF10 |
| Añadido por el equipo (buenas prácticas) | RNF11 |

## Pendientes

- Confirmar las cinco decisiones DA1 a DA5.
- Confirmar las cifras propuestas: 5 MB (RF11), 10 s (RF8), 5 minutos (RF23), 2 s y tamaño de datos (RNF4), longitud de la contraseña (RF4).
- Definir cómo se accede al registro del CONADIS.
