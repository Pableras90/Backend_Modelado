# Bootcamp Backend-Modelado documental



## Estructura general del sistema

El portal de ELearning estará orientado al mundo de la programación y se compone de cursos que contienen videos y artículos relacionados. Los recursos multimedia se almacenarán en un storage S3 y un headless CMS, mientras que en la base de datos se registrarán los identificadores de estos recursos. A continuación se presenta el modelo de datos detallado.

## Entidades principales

### Autor

- **ID**: Identificador único del autor.
- **Biografía**: Objeto (Hacemos uso del Subset Pattern para optimizar nuestro Working Set).
- **Cursos**: Lista de cursos en los que participan los autores. 
  
### Biografía(Objeto relacionado con autor)

- **Nombre**: Nombre del autor.
- **Página de Biografía**: URL de la página que muestra la biografía completa del autor.

### Curso

- **ID**: Identificador único del curso.
- **Nombre**: Título del curso.
- **Descripción**: Descripción del curso.
- **Fecha de publicación**: Fecha con la publicación del curso.
- **Ultimos Cursos**: Lista con el ID de los ultimos cursos para optimizar el Working Set.

### Video

- **ID**: Identificador único del video.
- **Nombre**: Título del video.
- **Autor**: Autor del video.
- **Curso**: Curso al que pertenece el video.(Por restricción de que incialmente no se compartirán videos entre cursos)
- **Temática**: Temática del video.
- **IdS3**: URL del video almacenado en el storage S3.
- **IdCMS**: URL del video almacenado en el headless CMS.

### Artículo

- **ID**: Identificador único del artículo.
- **Curso**: Curso al que pertenece el artículo.
- **Nombre**: Título del artículo.
- **IdS3**: URL del contenido del artículo almacenado en el storage S3.
- **IdCMS**: URL del contenido del artículo almacenado en el headless CMS.
- **Autor**: Autor del artículo.

### Temática

- **ID**: Identificador único de la temática.
- **Nombre**: Nombre de la temática.

## Relaciones

- Un curso puede tener varios autores y un autor puede tener varios cursos (relación muchos a muchos entre Curso y Autor).
- Un video tiene un único autor y un autor puede tener varios videos (relación uno a muchos entre Autor y Video).
- Un video tiene una temática y una temática puede tener varios videos (relación uno a muchos entre Temática y Video).
- Un artículo puede tener varios autores y un autor puede tener varios artículos (relación muchos a muchos entre Artículo y Autor).
- Un curso puede tener varios artículos (relación uno a muchos entre Curso y Artículos).

