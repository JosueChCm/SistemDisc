# Stack y reglas técnicas — Sistema de Gestión de Ajustes Razonables (Bienestar Universitario)

Redacta todos los documentos en español.

## Decisiones vigentes (ADR-001, ADR-002)

- Estilo arquitectónico: monolito modular por dominio con HTML generado en servidor (PA-02). Modelo C4 en ADR-002.
- Framework: CodeIgniter 4, versión estable vigente [VERIFICAR en semana 7]. Alternativa de reversión: Laravel (criterios en ADR-001).
- Lenguaje: PHP 8.x según la versión que incluya el XAMPP del laboratorio [VERIFICAR]. Composer: sí [VERIFICAR].
- Base de datos: MySQL 8 (o la MariaDB que incluya el XAMPP del laboratorio [VERIFICAR]). Collation `utf8mb4_unicode_ci`. Motor InnoDB.
- Servidor web: Apache de XAMPP. La raíz pública es la carpeta `public/` del proyecto [VERIFICAR configuración de VirtualHost o acceso vía `/public`].
- Seguridad de red: TLS 1.2 o superior en Apache (RNF5) [VERIFICAR configuración en el laboratorio]; acceso solo desde la red de la universidad.
- Repositorio de archivos: carpeta fuera de la raíz pública con los Documentos Acreditadores en PDF cifrados (RF10 a RF12, RNF6).
- Control de versiones: GitHub. Ramas `main` (estable), `develop` (integración), `feature-<modulo>` (trabajo).
- Pruebas: PHPUnit [VERIFICAR]; `axe-core` con Playwright para accesibilidad y teclado; NVDA y JAWS de forma manual. Las propiedades P1 a P14 de `design.md` se implementan como pruebas parametrizadas en PHPUnit [INFERIDO].

## Módulos de la aplicación (ADR-002)

| Módulo | Carpeta | Requisitos |
|---|---|---|
| Autenticación y perfiles | `autenticacion/` | RF41–RF44 |
| Registro de estudiantes | `estudiantes/` | RF1–RF5 |
| Validación del CONADIS | `validacion_conadis/` | RF6–RF9 |
| Documentos acreditadores | `documentos/` | RF10–RF12 |
| Solicitudes de ajuste (incluye formulario, pendientes y vista del Estudiante) | `solicitudes/` | RF13–RF19, RF26–RF30, RF35, RF45–RF51 |
| Estados y aviso al docente | `estados/` | RF20–RF25 |
| Decisión del docente | `decision_docente/` | RF36–RF40 |
| Reportes semestrales | `reportes/` | RF31–RF34 |

## Convenciones de nombres

- Idioma: español en nombres de dominio, rutas, tablas y vistas; inglés solo en palabras reservadas del framework.
- Base de datos: `snake_case`, singular (`usuario`, `estudiante`, `asignatura`, `tipo_ajuste`, `solicitud`, `decision_docente`, `documento_acreditador`).
- Clases: `PascalCase` (`SolicitudAjuste`, `DecisionDocente`). Rutas: `kebab-case` (`/mis-solicitudes`, `/reporte-semestral`, `/docente/solicitudes`).
- Valores de estado en minúscula, como en el DDL: `recibida`, `evaluada`, `observada`, `aprobada`, `implementada`.

## Reglas inviolables

- Secretos (credenciales de base de datos, clave de cifrado, secreto de sesión, credenciales de correo y del CONADIS) viven solo en `.env`; `.env` no se versiona nunca (RNF11).
- Todo módulo nuevo debe trazar a un RF, RNF o historia H1 a H6 de `requirements.md`; si no traza, no se construye.
- Toda tabla nueva o modificada obliga a actualizar `docs/arquitectura/modelo_datos.md` en el mismo commit.
- El Número CONADIS, el Tipo de Discapacidad y los Documentos Acreditadores se almacenan cifrados (RNF6); las contraseñas con hash; ninguno aparece en registros ni en logs (RNF10).
- Solo la Oficina cambia el Estado de una Solicitud (RF22); el Docente nunca recibe datos de discapacidad (RNF8).
- Consentimiento y finalidad (Ley N.° 29733): `requirements.md` solo asume que la Oficina informa la finalidad antes de registrar. Un registro de consentimiento con fecha y finalidad es una propuesta [INFERIDO]; requiere un RF nuevo antes de construirse.
- Ningún dato personal real en el desarrollo ni en las pruebas: solo datos simulados (RNF9).
- Toda pantalla pasa `axe-core` sin infracciones A/AA y se completa solo con teclado antes de integrarse a `develop` (RNF1, RNF2).
- Los mensajes de error se redactan en español, tal como figuran en `requirements.md`.

## Parámetros propuestos por confirmar

Definidos en `requirements.md`: límite de 5 MB por PDF (RF11), espera máxima de 10 s al CONADIS (RF8), correo dentro de 5 minutos (RF23), 2 s en el percentil 95 con 500 Estudiantes y 3000 Solicitudes (RNF4), contraseña temporal de 12 caracteres (RF4).

## FRONTERA DE ALCANCE

- NO implementar servidor MCP ni modelo de lenguaje: el sistema no los usa (DA4). No se crea módulo `asistente/`; cualquier código de IA es un error.
- NO implementar: adjuntos distintos del Documento Acreditador; sincronización con el CONADIS (solo validación por consulta); notificaciones distintas del correo al docente (incluidos WhatsApp y avisos al Estudiante); integración con matrícula o SUNEDU; evaluación médica; aplicación móvil; horarios y asignación de aulas.
- NO implementar historial de estados, estado "rechazada" ni control de duplicados por Número CONADIS: el D0 no los pide.

## Divergencias por resolver

`ADR-001` y `ADR-002` usan PHP, CodeIgniter 4, MySQL 8 y XAMPP; el D0, `requirements.md` y `design.md` están escritos para otra pila.

| Tema | ADR-001 y ADR-002 (este archivo) | D0, `requirements.md` y `design.md` |
|---|---|---|
| Lenguaje y framework | PHP 8, CodeIgniter 4 | Python 3.11+, FastAPI |
| Base de datos | MySQL 8 | SQLite (el DDL está en SQLite) |
| Plazo | 8 semanas | 10 semanas |
| Pruebas de propiedades | PHPUnit parametrizado | `hypothesis` |
| Despliegue | Apache de XAMPP | `uvicorn` tras el servidor web de la universidad |

Hasta decidir, el DDL de `design.md` y las firmas Python sirven como referencia de contrato y deben traducirse. Si el equipo vuelve a la pila del D0, se reemplazan las secciones «Decisiones vigentes» y «Módulos»; las reglas inviolables y la frontera de alcance no cambian.
