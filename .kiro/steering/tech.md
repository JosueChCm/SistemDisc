# Tecnología · Gestión de ajustes razonables para estudiantes con discapacidad (Bienestar Universitario)

Redacta todos los documentos en español.

## Pila de referencia (fijada en el D0; no proponer alternativas sin justificación)
- **Lenguaje:** Python 3.11+.
- **Backend:** FastAPI.
- **Frontend:** página web simple (HTML + JavaScript). El formulario de solicitud usa calendario emergente y selección de asignaturas mediante arrastrar y soltar.
- **Base de datos:** SQLite, con los datos reales de los estudiantes atendidos por la oficina en el semestre anterior (para agilizar las pruebas).
- **Despliegue:** aplicación web de uso interno, accesible solo desde la red de la universidad. Acceso con código o correo institucional.
- **Control de versiones:** Git y GitHub.

## Restricciones técnicas
- La aplicación debe ser accesible para personas con discapacidad visual y funcionar correctamente con lectores de pantalla.
- El sistema debe ser rápido y seguro: cargar las páginas en poco tiempo y proteger los datos de los estudiantes mediante encriptación.
- El número CONADIS ingresado se valida automáticamente contra el registro nacional del CONADIS.
- Los certificados (CONADIS o médico) se adjuntan en PDF al registrar al estudiante.
- Al aprobarse una solicitud se envía un correo automático al docente de la asignatura.
- El reporte con el total de solicitudes por tipo de ajuste se muestra en un gráfico de barras.
- El sistema no evalúa la pertinencia médica del ajuste ni sustituye la decisión de la oficina.

## No definido en el D0
Modelo de lenguaje, recuperación (RAG), servidor MCP, salidas estructuradas, registro de trazas, gestión de claves y de variables de entorno, método de autenticación, librería de gráficos y servicio de correo. No se asume ninguna tecnología para estos puntos hasta que se definan.
