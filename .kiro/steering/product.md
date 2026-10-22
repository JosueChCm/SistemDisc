# Producto · Gestión de ajustes razonables para estudiantes con discapacidad (Bienestar Universitario)

Redacta todos los documentos (requisitos, diseño, tareas) y todas las respuestas en español.

## Propósito
Centralizar en una aplicación web interna el registro y el seguimiento de las solicitudes de ajustes razonables de los estudiantes con discapacidad de la UNDC, para que la Oficina de Bienestar Universitario no pierda solicitudes, sepa cuáles están pendientes, pueda informar al docente qué ajuste corresponde a cada estudiante y genere el reporte que exigen la Ley N.° 29973 y la Ley Universitaria N.° 30220.

## Usuarios
- **Estudiante con discapacidad** (principal): registra su solicitud de ajuste razonable para una asignatura y conoce si fue aprobada. Los estudiantes con discapacidad visual usarán el formulario de solicitud.
- **Oficina de Bienestar Universitario**: registra estudiantes, cambia el estado de las solicitudes, lista lo pendiente y obtiene el reporte semestral.
- **Docente**: aprueba o rechaza los ajustes solicitados para su asignatura.

## Capacidades del producto
1. Registro del estudiante con su tipo de discapacidad y el documento que la acredita (certificado CONADIS o certificado médico, en PDF).
2. Registro de solicitudes de ajuste razonable por asignatura (tiempo adicional en evaluaciones, materiales en formato accesible, intérprete de lengua de señas peruana, aula en primer piso, mobiliario adaptado, acompañamiento en laboratorio), ingresadas por el estudiante o por la oficina.
3. Cambio de estado de la solicitud (recibida, evaluada, observada, aprobada, implementada) con aviso por correo al docente de la asignatura.
4. Listado de solicitudes pendientes.
5. Reporte con el total de solicitudes por tipo de ajuste, presentado en un gráfico de barras, para el reporte anual.
6. Formulario de solicitud compatible con lectores de pantalla.

## Reglas no negociables
- **Accesibilidad:** la aplicación debe ser accesible para personas con discapacidad visual y funcionar correctamente con lectores de pantalla.
- **Rendimiento y seguridad:** el sistema debe ser rápido y seguro, cargar las páginas en poco tiempo y proteger los datos de los estudiantes mediante encriptación.
- **Interfaz:** debe ser amigable e intuitiva para todos los usuarios; el formulario usa calendario emergente y selección de asignaturas mediante arrastrar y soltar.
- **Validación:** el número CONADIS ingresado se valida automáticamente contra el registro nacional del CONADIS.
- **Límite de decisión:** el sistema no evalúa la pertinencia médica del ajuste ni sustituye la decisión de la oficina.
- **Acceso:** uso interno, solo desde la red de la universidad; el personal y los estudiantes acceden con código o correo institucional.
- **Datos de prueba:** para agilizar las pruebas se emplean los datos reales de los estudiantes atendidos por la oficina en el semestre anterior.

## Restricciones técnicas
Python 3.11+, FastAPI, frontend HTML y JavaScript simple, SQLite, Git y GitHub para el control de versiones.

## Fuera de alcance (semestre 2026-II)
Carga o almacenamiento de archivos adjuntos (certificados, informes médicos), integración con CONADIS, con el sistema académico de matrícula o con SUNEDU, notificaciones automáticas por correo o WhatsApp, evaluación médica o calificación de la discapacidad, aplicación móvil nativa, y programación de horarios y asignación de aulas.
