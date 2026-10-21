# quarkus-tasks-demo

Aunque el nombre sugiere una aplicación de tareas, el código actual es una plantilla de saludo: solo expone `GET /hello`. No hay todavía modelo, persistencia ni operaciones CRUD de tareas.

## Guías adaptadas

- [Creating Your First Application](https://quarkus.io/guides/getting-started): configuración Maven/Quarkus y ejecución en modo de desarrollo.
- [Writing REST Services with RESTEasy Reactive](https://quarkus.io/guides/rest): recurso REST sencillo con `@Path`, `@GET` y tipo de respuesta.

El proyecto tiene las dependencias `quarkus-rest` y `quarkus-rest-jackson`, pero el endpoint actual devuelve texto plano (`text/plain`); todavía no adapta una API JSON. Tampoco usa RESTEasy Classic: para comparar, consulta [la guía clásica](https://es.quarkus.io/guides/resteasy), teniendo en cuenta que el código usa Quarkus REST.

## Probar

Requiere Java 21 según `maven.compiler.release` en `pom.xml`.

```powershell
.\mvnw.cmd quarkus:dev
```

En otra terminal:

```powershell
curl.exe -i http://localhost:8080/hello
```

La respuesta esperada es HTTP 200 con el texto `Hello from Quarkus REST`. Ejecuta las pruebas automatizadas con:

```powershell
.\mvnw.cmd test
```

## Ejercicio práctico

Para convertir esta plantilla en una API de tareas:

1. Crea un modelo `Tarea` con campos como `id`, `titulo` y `completada`.
2. Añade un recurso con endpoints para listar y crear tareas.
3. Usa `@Consumes(MediaType.APPLICATION_JSON)` y `@Produces(MediaType.APPLICATION_JSON)`.
4. Prueba un `GET` y un `POST` con un cliente HTTP y agrega pruebas RestAssured.

Al completar esos pasos, documenta la adaptación JSON y, si agregas restricciones, la guía de [validación](https://quarkus.io/guides/validation). Esos comportamientos aún no existen en este proyecto.
