# Alcance del producto: blog de robótica

## Incluido

1. **Portada:** mostrar el nombre del blog y los artículos publicados más recientes, ordenados del más nuevo al más antiguo. Cada artículo incluye título, fecha, extracto y enlace a su página. Si no hay publicaciones, mostrar un mensaje informativo.
2. **Lectura de artículos:** ofrecer una página individual con título, fecha de publicación, autoría y contenido organizado en párrafos y subtítulos. Las rutas de artículos inexistentes deben responder con una página 404.
3. **Sobre mí:** incluir una página con una presentación breve del autor, editable para sustituir el texto de ejemplo.
4. **Navegación:** proporcionar enlaces claros entre la portada y «Sobre mí», así como una forma de volver a la portada desde cada artículo. La navegación básica no dependerá de JavaScript.
5. **Gestión de contenido:** permitir al editor crear, actualizar y retirar artículos y modificar la presentación del autor mediante el panel administrativo estándar de Django. Los artículos no publicados no se mostrarán públicamente.
6. **Contenido inicial:** incluir artículos de ejemplo relacionados con robótica y una presentación de ejemplo, reemplazables o eliminables por el editor.
7. **Diseño y accesibilidad:** ofrecer páginas adaptables a móviles y ordenadores, legibles y accesibles, con HTML semántico, encabezados coherentes, enlaces descriptivos y uso por teclado.

## Fuera de alcance

- Cuentas, perfiles o registro para lectores.
- Comentarios.
- Suscripciones o boletines.
- Buscador.
- Flujos editoriales avanzados, como revisión, programación de publicaciones o múltiples roles.
- Funciones de interacción social.
- JavaScript para las funciones principales de lectura y navegación.

## Contenido y datos

### Artículos

Cada artículo tendrá como mínimo título, slug legible para la URL, contenido, autoría, fecha de publicación y estado de publicación. Solo los artículos publicados aparecerán en las páginas públicas; los borradores estarán disponibles para el editor autenticado desde el panel administrativo.

### Presentación del autor

La primera versión tendrá una única presentación breve del sitio, editable desde el panel administrativo.

## Rutas previstas

- `/` — portada y artículos recientes.
- `/sobre-mi/` — presentación del autor.
- `/articulos/<slug>/` — página de un artículo.
- `/admin/` — panel administrativo restringido a usuarios autorizados.

## Criterios de calidad

- Las páginas deben funcionar en pantallas pequeñas y grandes sin desplazamiento horizontal innecesario.
- La tipografía, el contraste, el espaciado y la longitud de línea deben favorecer la lectura.
- Las páginas informativas se renderizarán en el servidor con Django y evitarán dependencias de JavaScript innecesarias.
- Las rutas inválidas de artículos devolverán una respuesta HTTP 404 adecuada.
- Las operaciones de edición estarán restringidas a usuarios autorizados; no habrá registro público.

## Límites y decisiones técnicas

- El sitio se implementará con Django, vistas y plantillas renderizadas en el servidor.
- Los artículos y la presentación del autor se gestionarán mediante modelos Django y el panel administrativo estándar.
- Se contempla SQLite para el desarrollo inicial; la base de datos de producción dependerá del entorno de despliegue.
- La identidad visual, el contenido definitivo, el dominio y el entorno de despliegue quedan por definir.