# EvaluatorIA

Admisión de solicitudes de movilidad y baremo de idiomas, con cada comprobación a la vista. Aplicación web de un solo fichero.

**Usar la app:** https://fborrasumh.github.io/evaluatoria/

**Idiomas:** español (por defecto), inglés, portugués; selector en la barra superior (o `?lang=en` / `?lang=pt` en la URL).

## Qué hace

Revisa la documentación de cada solicitud de una convocatoria de movilidad y prepara el listado de admitidas y excluidas. Viene configurada para la convocatoria Erasmus+ estudios 2026/2027 de la UMH (BOUMH 5/12/2025), con los criterios editables y exportables para otras convocatorias.

- **Lee la carpeta tal como sale de Drive** (ZIP o carpeta, una subcarpeta por solicitante): desempaqueta los `.xsig` de la sede electrónica (el PDF va dentro en base64), lee los justificantes de registro (fecha, documentos adjuntos, subsanaciones y cambios de destino) y avisa si el justificante cita documentos que no están en la carpeta.
- **Seis comprobaciones por solicitud:** solicitud firmada (firma digital en el PDF o trazo dentro del recuadro de firma, medido por código), DNI/NIE/pasaporte en vigor a la fecha de referencia, extracto del expediente, acreditación de idiomas, CV si algún destino tiene entrevista (según el catálogo de plazas leído del PDF de las bases) y certificación Buddy.
- **Idiomas:** idioma, nivel, centro que expide, fecha de expedición y titular de cada certificado, y los puntos por destino según la base 8 (inglés + idioma del país), con las equivalencias EOI e IRIS.
- **Nombre del titular:** compara el nombre del certificado con el del solicitante sin tildes ni orden; si coinciden los apellidos pero no el nombre, lo marca como «posible familiar» y no suma puntos hasta que se revisa.
- **Fases provisional y definitiva:** la definitiva suma las subsanaciones y usa los destinos nuevos si cambiaron.
- **Propone, no decide:** admitida, excluida o pendiente con su motivo; el personal confirma cada decisión.
- **Descargas:** listado de admitidas y excluidas (Word y CSV, con el documento enmascarado), hoja de idiomas (CSV), un informe Word por solicitud (ZIP) y el trabajo completo (JSON).
- **Ejemplo sin clave** con cinco solicitantes ficticios.

## Cómo se usa la IA

Con la propia clave de OpenAI, Google Gemini o Anthropic Claude (modelo con visión). La clave se guarda solo en el navegador. No hace falta servidor.

La IA solo lee lo que el código no puede: la fecha de caducidad, el número y el titular del documento de identidad escaneado, y el idioma, nivel, centro, fecha y titular de cada certificado (y el recuadro de firma cuando el trazo es dudoso). El código valida lo que devuelve: fechas reales, niveles de una escala cerrada, número de documento frente al de la carpeta, nombre del titular, cita literal y nivel presentes en el texto del certificado. Lo dudoso queda «pendiente» y no suma.

## Privacidad

Las solicitudes se leen en el navegador y no se suben a ningún sitio. Del formulario de solicitud no se guarda el texto (lleva IBAN, dirección y teléfono): solo los destinos y el recorte del recuadro de firma.

Solo al pulsar «Leer con IA», y tras un aviso con una muestra de lo que sale, se envía al proveedor elegido: la imagen del documento de identidad (1-2 páginas) y la de los certificados escaneados (las imágenes no se pueden enmascarar), el texto de los certificados que lo tienen con nombre, correo, DNI y teléfono enmascarados, y el recuadro de firma si el código duda. Nunca la solicitud completa. El nombre del solicitante no va en las instrucciones: la coincidencia del titular se comprueba en el navegador.

Al recargar la página se conservan las lecturas y las decisiones, pero no los ficheros: para leer con IA o ver documentos hay que volver a arrastrar la carpeta. Antes de usarla con datos reales, consulta con la Delegación de Protección de Datos si el proveedor de IA elegido es aceptable para documentos de identidad.

## Límites

- Es una herramienta de apoyo: no sustituye la revisión del Servicio ni produce resoluciones.
- La firma manuscrita se detecta por trazo dentro del recuadro; no se verifica su autoría. Si la solicitud es un escaneo sin texto, la firma y los destinos se revisan a mano (los destinos se pueden escribir en la app).
- La IA puede leer mal un escaneo de baja calidad: revisa siempre los certificados «leídos de imagen» y los marcados como pendientes.
- Las plazas con entrevista se detectan por la palabra «Entrevista» junto a la plaza en el PDF de las bases; la lista debe revisarse en el paso 2.
- Probada con datos ficticios en el formato de la sede, con dos expedientes reales en local (sin clave de IA) y con IA simulada; no se ha probado aún con una clave real.

## Autoría

Fernando Borrás Rocher (Universidad Miguel Hernández de Elche).

A partir de la necesidad y los criterios de revisión del Servicio de Relaciones Internacionales y Cooperación de la UMH (convocatoria Erasmus+ estudios 2026/2027).

ORCID: Fernando Borrás Rocher [0000-0002-5519-4573](https://orcid.org/0000-0002-5519-4573)

## Cómo citar

Borrás Rocher, F. (2026). *EvaluatorIA* (v1.0.0) [Software]. (DOI en trámite)

## Licencia

MIT. Véase [LICENSE](LICENSE).
