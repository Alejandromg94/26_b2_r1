# 🎓 Proyecto - Sistema de Gestión de Estudiantes

Este es un proyecto backend desarrollado con **Java 21** y **Spring Boot** para la gestión de estudiantes. Incluye una API RESTful que permite crear, leer, actualizar y eliminar (CRUD) registros de estudiantes, persistiendo los datos en una base de datos **PostgreSQL**.

## 🚀 Tecnologías Utilizadas

- **Java 21**: Lenguaje de programación.
- **Spring Boot 3.x**: Framework para el desarrollo de la aplicación.
- **Maven**: Gestor de dependencias y construcción.
- **PostgreSQL**: Base de datos relacional.
- **Lombok**: Librería para reducir el código boilerplate.
- **Spring Data JPA**: Abstracción para la capa de persistencia.

## 🔌 Endpoints de la API

| Método | Endpoint                      | Descripción                   |
| :----- | :---------------------------- | :---------------------------- |
| GET    | `/api/students`               | Obtener todos los estudiantes |
| GET    | `/api/students/{id}`          | Obtener estudiante por ID     |
| GET    | `/api/students/email/{email}` | Obtener estudiante por Email  |
| POST   | `/api/students`               | Crear un nuevo estudiante     |
| PUT    | `/api/students/{id}`          | Actualizar un estudiante      |
| DELETE | `/api/students/{id}`          | Eliminar un estudiante        |

---

## 🧪 Laboratorio: Documentación de Pruebas de API REST

### 1. Crear un nuevo estudiante

- **Método:** `POST` | **URL:** `http://localhost:8080/api/students`
- **Respuesta:**

```json
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
Método: GET | URL: http://localhost:8080/api/students

Código de Estado: 200 OK

3. Buscar estudiante por ID (Existente)
Método: GET | URL: http://localhost:8080/api/students/7

Código de Estado: 200 OK

4. Buscar estudiante por Email
Método: GET | URL: http://localhost:8080/api/students/email/vicky@gmail.com

Código de Estado: 200 OK

5. Actualizar datos del estudiante
Método: PUT | URL: http://localhost:8080/api/students/7

Respuesta:

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

6. Escenario de Error: Buscar ID inexistente
Método: GET | URL: http://localhost:8080/api/students/999

Respuesta: {"status": 404, "message": "Student not found with id 999"}

Código de Estado: 404 Not Found

7. Eliminar el registro
Método: DELETE | URL: http://localhost:8080/api/students/7

Código de Estado: 204 No Content

📝 Cuestionario de Análisis
1. Diferencia entre estados 200 y 201:
El 200 OK indica éxito general en lecturas o actualizaciones. El 201 Created confirma específicamente que se ha generado un nuevo recurso en la base de datos (usado en POST).

2. Importancia del 404 vs 500:
El 404 informa al cliente (frontend) que el recurso buscado no existe, permitiendo una gestión elegante del error. Un 500 implica un fallo técnico interno del servidor, siendo mucho más crítico y grave.

3. ¿Qué pasa en la base de datos al hacer DELETE?
Se ejecuta una instrucción SQL DELETE FROM students WHERE id = ?. El registro se elimina físicamente de la tabla y deja de persistir en el sistema.

4. ¿Qué pasa al intentar crear un email duplicado?
Si existe una restricción UNIQUE en la base de datos, esta fallará. El código de error más adecuado es 409 Conflict, que notifica al usuario que los datos intentan colisionar con otros ya existentes.

5. ¿Por qué PUT y no POST para actualizar?
Por la Idempotencia. PUT garantiza que, aunque se envíe la misma solicitud varias veces, el estado final será el mismo. POST no garantiza esto, ya que su propósito semántico es la creación de nuevos recursos.
```
