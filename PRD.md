# PRD: Blog de robótica

## 1. Resumen

Crear un blog de robótica sencillo y centrado en la lectura. Los visitantes podrán descubrir artículos recientes, leer cada publicación completa y conocer a quien escribe en una sección «Sobre mí». El sitio será adaptable a móviles y ordenadores, y el autor podrá mantener el contenido mediante el panel administrativo de Django sin editar plantillas.

## 2. Objetivo y contexto

El blog ofrece a las personas interesadas en robótica un lugar claro y fácil de consultar para leer y seguir artículos. La experiencia prioriza el contenido y una navegación sencilla; el diseño y la estructura deben facilitar la lectura y el acceso desde distintos dispositivos.

## 3. Usuarios

- **Visitante:** persona interesada en leer artículos de robótica y conocer al autor. No necesita una cuenta.
- **Autor y editor del sitio:** persona que comparte sus conocimientos y gestiona los artículos y la presentación del autor desde Django Admin.

No habrá registro público ni perfiles de lectores. El panel administrativo estará reservado a usuarios autorizados.

## 4. Alcance del producto

### Incluido

1. Portada con el nombre del blog y los artículos publicados más recientes, ordenados del más nuevo al más antiguo. Cada artículo incluirá título, fecha, extracto y enlace a su página.
2. Página individual por artículo, con título, fecha de publicación, autoría y contenido organizado en párrafos y subtítulos.
3. Página «Sobre mí» con una presentación breve del autor.
4. Navegación clara entre la portada y «Sobre mí», y un enlace para volver a la portada desde cada artículo.
5. Diseño adaptable, legible y accesible, con prioridad en el contenido.
6. Artículos y presentación iniciales de ejemplo que el autor pueda sustituir o eliminar.
7. Gestión básica de artículos y de la presentación mediante el panel administrativo estándar de Django.

### Excluido

- Cuentas o perfiles para lectores y registro público.
- Comentarios.
- Suscripciones o boletines.
- Buscador.
- Flujos editoriales avanzados, como revisión, programación de publicaciones o múltiples roles.
- Funciones de interacción social.
- JavaScript para las funciones principales de lectura y navegación.

## 5. Requisitos funcionales

### RF-01: Mostrar la portada

La portada debe mostrar el nombre del blog y una lista de artículos publicados, ordenados cronológicamente del más nuevo al más antiguo. Cada elemento debe incluir título, fecha, extracto y enlace al artículo completo.

**Criterios de aceptación**

- Al visitar la ruta raíz, se muestra la portada.
- Solo aparecen artículos publicados y se muestran en orden descendente por fecha de publicación.
- Cada artículo de la lista permite abrir su página individual.
- Si no hay artículos publicados, se muestra un mensaje informativo.

### RF-02: Leer un artículo

Cada artículo debe tener una página propia que muestre título, fecha de publicación, autoría y contenido. El contenido debe conservar una estructura legible con párrafos y subtítulos.

**Criterios de aceptación**

- La página muestra los datos del artículo disponibles: título, fecha, autoría y contenido.
- Los párrafos y subtítulos del contenido se presentan de forma estructurada.
- Un artículo no existente devuelve una página de no encontrado con estado HTTP 404.

### RF-03: Consultar «Sobre mí»

La página «Sobre mí» debe presentar brevemente al autor y permitir reemplazar el texto de ejemplo.

**Criterios de aceptación**

- Existe una página identificable como «Sobre mí».
- La navegación principal incluye un enlace claro a esta página.
- El autor puede modificar el texto de presentación desde el panel administrativo.

### RF-04: Navegar por el sitio

Las páginas deben ofrecer navegación sencilla entre la portada, los artículos y «Sobre mí».

**Criterios de aceptación**

- Los enlaces principales funcionan desde las páginas del sitio.
- Los enlaces tienen nombres claros y comprensibles.
- Desde cada artículo se puede volver a la portada.
- La navegación básica funciona sin JavaScript.

### RF-05: Gestionar contenido

El autor/editor podrá crear, editar y retirar artículos y actualizar la presentación de «Sobre mí» mediante el panel administrativo estándar de Django.

**Criterios de aceptación**

- El panel administrativo permite gestionar artículos y la presentación del autor.
- Los artículos no publicados no aparecen en las páginas públicas.
- Solo usuarios autorizados pueden acceder a las operaciones de edición.
- No se ofrece un proceso de registro público.

## 6. Requisitos de contenido y datos

### Artículo

Cada artículo tendrá, como mínimo:

- Título.
- Identificador legible para la URL (slug).
- Contenido.
- Autoría.
- Fecha de publicación.
- Estado de publicación.

Los artículos publicados se mostrarán en las páginas públicas. Los borradores no estarán disponibles para visitantes y serán gestionables por el autor/editor autorizado desde el panel administrativo.

### Presentación del autor

La página «Sobre mí» tendrá un texto breve editable. En la primera versión habrá una única presentación principal.

### Contenido inicial

La entrega incluirá artículos de ejemplo relacionados con robótica y un texto de presentación. Ambos podrán sustituirse o eliminarse desde la gestión de contenido.

## 7. Requisitos no funcionales

- **Adaptabilidad:** las páginas deben poder utilizarse en pantallas pequeñas y grandes sin desplazamiento horizontal innecesario.
- **Legibilidad:** tipografía, contraste, espaciado y longitud de línea deben favorecer la lectura prolongada.
- **Accesibilidad:** utilizar HTML semántico, estructura de encabezados coherente, enlaces descriptivos y navegación usable con teclado.
- **Rendimiento:** las páginas informativas se renderizarán en el servidor con Django y evitarán dependencias de JavaScript innecesarias.
- **Robustez:** las rutas de artículos inexistentes deben mostrar una respuesta HTTP 404 adecuada.
- **Seguridad:** las operaciones de edición no estarán disponibles para visitantes anónimos; se seguirán las prácticas de seguridad de Django para producción.

## 8. Propuesta técnica

- **Backend y renderizado:** Django, con vistas y plantillas renderizadas en el servidor.
- **Persistencia:** modelos Django y migraciones para artículos y presentación del autor.
- **Gestión editorial:** Django Admin, restringido a usuarios autorizados.
- **Interfaz:** plantillas HTML semánticas y CSS adaptable; no se necesita JavaScript para las funciones principales.
- **Base de datos:** SQLite para el desarrollo inicial. La elección para producción dependerá del entorno de despliegue.

La estructura exacta de aplicaciones, las versiones de Django y la configuración de despliegue se decidirán durante la implementación.

## 9. Rutas propuestas

- `/` — portada y artículos recientes.
- `/sobre-mi/` — presentación del autor.
- `/articulos/<slug>/` — detalle de un artículo.
- `/admin/` — panel administrativo de Django, con acceso restringido a usuarios autorizados.

## 10. Métricas de éxito

- Un visitante puede encontrar un artículo desde la portada, abrirlo y leerlo completo.
- Un visitante puede encontrar y consultar la sección «Sobre mí».
- Las páginas se pueden utilizar en móvil y escritorio sin perder contenido ni navegación.
- El autor/editor puede actualizar los artículos y la presentación sin editar las plantillas.

## 11. Supuestos y decisiones pendientes

- El tema del contenido es la robótica y el idioma inicial del sitio será el español.
- En la primera versión, el autor también será responsable de gestionar el contenido; habrá una presentación principal del autor.
- El dominio, la identidad visual, el contenido definitivo y el entorno de despliegue todavía no están definidos.
- La selección de base de datos para producción dependerá del entorno donde se publique el sitio.
