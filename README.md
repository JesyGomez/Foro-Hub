# API REST para Gestión de Tópicos

Este proyecto implementa una API REST utilizando **Java 21** y **Spring Framework**. La API está diseñada para gestionar tópicos, permitiendo realizar operaciones CRUD (Crear, Leer, Actualizar, Eliminar).

## Características

- **Crear un nuevo tópico**
- **Mostrar todos los tópicos creados**
- **Mostrar un tópico específico**
- **Actualizar un tópico existente**
- **Eliminar un tópico**

Además, el proyecto incluye:

- Rutas diseñadas según las mejores prácticas del modelo REST.
- Validaciones para garantizar las reglas de negocio.
- Persistencia de datos mediante una base de datos relacional.
- Servicio de autenticación y autorización para proteger el acceso a la información.

## Tecnologías Utilizadas

- **Java 21**
- **Spring Boot**
- **Spring Data JPA**
- **Spring Security**
- **H2 Database** (para pruebas) o **MySQL** (para producción).
- **Maven** para la gestión de dependencias.
- **Postman** (recomendado para pruebas de la API).
- **Insomnia**
## Requisitos Previos

- **Java 21** instalado.
- **Maven** instalado.
- Un entorno de desarrollo como IntelliJ IDEA o Eclipse.
- Opcional: Docker (para ejecutar la base de datos en un contenedor).

## Instalación

1. Clona el repositorio:

   ```bash
   git clone https://github.com/JesyGomez/Foro-Hub.git
   cd foro-Hub
   ```

2. Configura la base de datos en el archivo `application.properties` o `application.yml`.

   ```properties
   spring.datasource.url=${DATASOURCE_URL}
   spring.datasource.username=${DATASOURCE_USERNAME}
   spring.datasource.password=${DATASOURCE_PASSWORD}
   spring.jpa.hibernate.ddl-auto=update
   ```

3. Compila y ejecuta el proyecto:

   ```bash
   mvn spring-boot:run
   ```

4. La API estará disponible en: `http://localhost:8080`

## Endpoints

| Método | Endpoint               | Descripción               |
|--------|------------------------|---------------------------|
| POST   | `/api/topicos`         | Crear un nuevo tópico.    |
| GET    | `/api/topicos`         | Listar todos los tópicos. |
| GET    | `/api/topicos/{id}`    | Obtener un tópico.        |
| PUT    | `/api/topicos/{id}`    | Actualizar un tópico.     |
| DELETE | `/api/topicos/{id}`    | Eliminar un tópico.       |

## Validaciones

- Los campos requeridos deben cumplirse al crear o actualizar un tópico.
- Las solicitudes deben cumplir las reglas de negocio definidas.

## Seguridad

El proyecto utiliza **Spring Security** para implementar un sistema de autenticación y autorización. Los usuarios deben autenticarse para acceder a los endpoints protegidos.

### Configuración del Servicio de Autenticación

- Uso de JWT (JSON Web Tokens) para la autenticación.
- Roles definidos para gestionar el acceso.

## Base de Datos

El proyecto utiliza **Spring Data JPA** para interactuar con la base de datos. Puedes usar:

- **H2 Database**: Configuración por defecto para pruebas.
- **MySQL**: Para entornos de producción. Configuración en `application.properties`.

### Esquema de la Base de Datos

- **Tópicos**
    - `id` (Long): Identificador único.
    - `titulo` (String): Título del tópico.
    - `descripcion` (String): Descripción del tópico.
    - `fechaCreacion` (Date): Fecha de creación.

## Pruebas

Se recomienda usar **Postman** o **Insomnia** para probar los endpoints de la API.

### Pruebas con Insomnia

Para realizar pruebas de los endpoints de la API, puedes usar **Insomnia** como herramienta de cliente REST. Sigue estos pasos:

#### Configuración de Insomnia

1. Descarga e instala [Insomnia](https://insomnia.rest/).
2. Crea un nuevo espacio de trabajo y selecciona "REST" como tipo.
3. Define las solicitudes correspondientes a los endpoints de la API:

| Método | Endpoint               | Descripción               | Ejemplo de Cuerpo (JSON)                                         |
|--------|------------------------|---------------------------|------------------------------------------------------------------|
| POST   | `/api/topicos`         | Crear un nuevo tópico.    | `{ "titulo": "Nuevo tema", "descripcion": "Descripción del tema" }` |
| GET    | `/api/topicos`         | Listar todos los tópicos. | _No requiere cuerpo._                                           |
| GET    | `/api/topicos/{id}`    | Obtener un tópico.        | _No requiere cuerpo._                                           |
| PUT    | `/api/topicos/{id}`    | Actualizar un tópico.     | `{ "titulo": "Título actualizado", "descripcion": "Nueva descripción" }` |
| DELETE | `/api/topicos/{id}`    | Eliminar un tópico.       | _No requiere cuerpo._                                           |

#### Ejemplo de Configuración de Headers

Asegúrate de incluir los headers necesarios, especialmente si estás utilizando autenticación. Por ejemplo:

- **Authorization**: `Bearer <tu-token-de-jwt>`
- **Content-Type**: `application/json`

#### Probar la API

1. Abre Insomnia y selecciona el endpoint que deseas probar.
2. Define el método (POST, GET, PUT, DELETE) y la URL del endpoint.
3. Si es necesario, incluye el cuerpo en formato JSON y los headers requeridos.
4. Envía la solicitud y verifica la respuesta.

## Contribuciones

¡Las contribuciones son bienvenidas! Por favor, sigue los siguientes pasos:

1. Haz un fork del repositorio.
2. Crea una nueva rama:

   ```bash
   git checkout -b mi-nueva-funcionalidad
   ```

3. Realiza los cambios y haz un commit:

   ```bash
   git commit -m "Agregada una nueva funcionalidad"
   ```

4. Sube los cambios a tu rama:

   ```bash
   git push origin mi-nueva-funcionalidad
   ```

5. Crea un pull request en GitHub.
