## Proyecto - Sistema de Gestión de Estudiantes

Este es un proyecto backend desarrollado con **Java 21** y **Spring Boot** para la gestión de estudiantes. Incluye una API RESTful que permite crear, leer, actualizar y eliminar (CRUD) registros de estudiantes, persistiendo los datos en una base de datos **PostgreSQL**.

## 🚀 Tecnologías Utilizadas

- **Java 21**: Lenguaje de programación.
- **Spring Boot 3.x**: Framework para el desarrollo de la aplicación.
- **Maven**: Gestor de dependencias y construcción.
- **PostgreSQL**: Base de datos relacional.
- **Lombok**: Librería para reducir el código boilerplate (Getters, Setters, etc.).
- **Spring Data JPA**: Abstracción para la capa de persistencia.

## 📋 Requisitos Previos

Asegúrate de tener instalado lo siguiente en tu entorno local:

- [Java JDK 21](https://www.oracle.com/java/technologies/downloads/#java21)
- [Maven](https://maven.apache.org/download.cgi)
- Cliente para probar la API (como [Postman](https://www.postman.com/) o [Insomnia](https://insomnia.rest/)).

## ⚙️ Configuración

La configuración de la base de datos se maneja a través de variables de entorno definidas en un archivo `.env` en la raíz del proyecto.

1.  Copia el archivo de ejemplo:

    ```bash
    copy .env.example .env
    ```

2.  Edita el archivo `.env` y define tus credenciales:
    ```ini
    DB_URL=jdbc:postgresql://localhost:5432/tu_base_de_datos
    DB_USERNAME=tu_usuario
    DB_PASSWORD=tu_contraseña
    ```

> **Nota:** El archivo `.env` está excluido del control de versiones para mantener tus credenciales seguras.

## 🛠️ Instalación y Ejecución (Windows)

1.  **Clonar el repositorio**:

    ```powershell
    git clone <url-del-repositorio>
    cd pi
    ```

2.  **Compilar el proyecto**:
    Asegúrate de estar en la raíz del proyecto y ejecuta:

    ```powershell
    .\mvnw.cmd clean install
    ```

    _Nota: Si tienes Maven instalado globalmente, puedes usar simplemente `mvn clean install`._

3.  **Ejecutar la aplicación**:

    ```powershell
    .\mvnw.cmd spring-boot:run
    ```

    La aplicación se iniciará en el puerto `8080` (por defecto).

## 🔌 Uso de la API (Endpoints)

La API base es `/api/students`. A continuación se detallan los endpoints disponibles:

### 1. Obtener todos los estudiantes

- **Método**: `GET`
- **URL**: `/api/students`
- **Respuesta**: Lista de estudiantes en formato JSON.

### 2. Obtener un estudiante por ID

- **Método**: `GET`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`

### 3. Obtener un estudiante por Email

- **Método**: `GET`
- **URL**: `/api/students/email/{email}`
- **Ejemplo**: `/api/students/email/ejemplo@correo.com`

### 4. Crear un nuevo estudiante

- **Método**: `POST`
- **URL**: `/api/students`
- **Body (JSON)**:
  ```json
  {
    "firstName": "Juan",
    "lastName": "Pérez",
    "email": "juan.perez@example.com",
    "birthDate": "2000-01-15",
    "phone": "1234567890"
  }
  ```

### 5. Actualizar un estudiante

- **Método**: `PUT`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`
- **Body (JSON)**:
  ```json
  {
    "firstName": "Juan Carlos",
    "lastName": "Pérez",
    "email": "juan.perez@example.com",
    "birthDate": "2000-01-15",
    "phone": "0987654321"
  }
  ```

### 6. Eliminar un estudiante

- **Método**: `DELETE`
- **URL**: `/api/students/{id}`
- **Ejemplo**: `/api/students/1`

## 🧪 Ejecutar Pruebas

Para ejecutar las pruebas unitarias y de integración, usa el siguiente comando:

```powershell
.\mvnw.cmd test
```

## 📂 Estructura del Proyecto

```
src/main/java/com/cesde/pi
├── controller    # Controladores REST (StudentController)
├── model         # Entidades JPA (Student)
├── repository    # Interfaces de Repositorio (StudentRepository)
├── service       # Lógica de Negocio (StudentService)
├── dto           # Objetos de Transferencia de Datos
└── exception     # Manejo de Excepciones Globales
```

🚀 Guía de Pruebas y Documentación

11. Crear un nuevo estudiante

Método: POST

URL: http://localhost:8080/api/students

Cuerpo (JSON):

JSON
{
"firstName": "Victoria",
"lastName": "Usma",
"email": "vicky@gmail.com",
"birthDate": "2000-01-15",
"phone": "2762426"
}
Respuesta del Servidor:

JSON
{
"id": 7,
"firstName": "Victoria",
"lastName": "Usma",
"email": "vicky@gmail.com",
"birthDate": "2000-01-15",
"phone": "2762426"
}
Código de Estado: 201 Created

2. Obtener la lista completa

Método: GET

URL: http://localhost:8080/api/students

Código de Estado: 200 OK

5. Actualizar datos del estudiante

Método: PUT

URL: http://localhost:8080/api/students/7

Cuerpo (JSON):

JSON
{
"firstName": "Victoria Eugenia",
"lastName": "Usma",
"email": "vicky@gmail.com",
"birthDate": "2000-01-15",
"phone": "3119998877"
}
Respuesta del Servidor:

JSON
{
"id": 7,
"firstName": "Victoria Eugenia",
"lastName": "Usma",
"email": "vicky@gmail.com",
"birthDate": "2000-01-15",
"phone": "3119998877"
}
Código de Estado: 200 OK

📝 Cuestionario de Análisis
Instrucciones: Responda las siguientes preguntas basándose en su experiencia durante el laboratorio y el código del proyecto.

¿Cuál es la diferencia entre los códigos de estado 200 y 201? ¿En qué endpoints se obtuvieron cada uno?
Respuesta:

El código de estado 200 OK indica que la solicitud fue procesada correctamente y el servidor devuelve la información solicitada. Se utiliza cuando no se crea un nuevo recurso, sino que simplemente se consulta, actualiza o elimina información existente.

En nuestro laboratorio, el código 200 OK se obtuvo en los siguientes endpoints:

GET /api/students (obtener todos los estudiantes)

GET /api/students/{id} (buscar por ID existente)

GET /api/students/email/{email} (buscar por email)

PUT /api/students/7 (actualizar estudiante)

Por otro lado, el código 201 Created indica que la solicitud fue exitosa y además se creó un nuevo recurso en el servidor.

En nuestro caso se obtuvo en:

POST /api/students (crear un nuevo estudiante)

La diferencia principal es que 200 confirma éxito general, mientras que 201 confirma creación exitosa de un nuevo recurso en la base de datos.

En el escenario de error (punto 6), ¿qué información devuelve la API y por qué es importante para un desarrollador frontend recibir un código 404 en lugar de un código 500?

Respuesta:

En el punto 6, cuando se intenta buscar un estudiante con un ID inexistente (/api/students/999), la API devuelve:

Código de estado: 404 Not Found

Un mensaje indicando que el estudiante no fue encontrado.

Ejemplo:

{
"status": 404,
"error": "Not Found",
"message": "Student not found with id 999"
}

Es importante devolver un 404 porque indica claramente que el recurso no existe. Esto le permite al desarrollador frontend:

Mostrar un mensaje amigable como: “El estudiante no existe”.

Evitar que la aplicación se bloquee.

Manejar correctamente el flujo del usuario.

En cambio, un 500 Internal Server Error indicaría que hay un problema interno del servidor, lo cual es más grave y sugiere un fallo en la aplicación, no simplemente un dato inexistente.

¿Qué sucede en la base de datos PostgreSQL cuando se ejecuta con éxito la petición DELETE? (Explique brevemente en términos de persistencia).
Respuesta:

Cuando se ejecuta correctamente la petición:

DELETE /api/students/3

La base de datos PostgreSQL elimina de manera permanente el registro correspondiente al estudiante con ID 3.

En términos de persistencia:

Se ejecuta una sentencia SQL similar a:

DELETE FROM students WHERE id = 3;

El registro deja de existir físicamente en la tabla.

Ya no podrá ser consultado posteriormente.

La operación queda guardada de forma permanente en la base de datos.

Por eso el servidor devuelve 204 No Content, indicando que la eliminación fue exitosa y no hay información adicional que devolver.

Si intentara crear un estudiante con el mismo email que ya existe en la base de datos, ¿qué cree que sucedería y qué código de error sería el más adecuado para devolver?
Respuesta:

Si el campo email está configurado como único en la base de datos (constraint UNIQUE), PostgreSQL no permitirá insertar otro registro con el mismo correo electrónico.

En ese caso:

La base de datos generaría un error de restricción.

La API debería capturar esa excepción.

El código de estado más adecuado sería:

409 Conflict

Este código indica que existe un conflicto con el estado actual del recurso (en este caso, el email ya está registrado).

También podría devolverse un mensaje como:

{
"status": 409,
"error": "Conflict",
"message": "Email already exists"
}

Esto permite al frontend informar al usuario que debe ingresar un correo diferente.

¿Por qué utilizamos el método PUT para actualizar y no el método POST? ¿Cuál es la convención técnica detrás de esta decisión?
Respuesta:

Se utiliza el método PUT para actualizar porque, según la convención REST:

POST se usa para crear nuevos recursos.

PUT se usa para actualizar un recurso existente.

La diferencia técnica principal es que:

POST no es idempotente → si se ejecuta varias veces puede crear múltiples recursos.

PUT es idempotente → si se ejecuta varias veces con los mismos datos, el resultado final será el mismo.

En nuestro caso:

PUT /api/students/7

Indica claramente que estamos modificando el recurso con ID 7.

Si usáramos POST para actualizar, estaríamos rompiendo la convención REST, ya que POST está diseñado para crear nuevos registros, no para modificar los existentes.
