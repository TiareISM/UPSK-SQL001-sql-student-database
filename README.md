# Student Database

## Learn SQL by Building a Student Database: Part 1

Este documento proporciona un registro detallado de las actividades realizadas y los comandos ejecutados durante la primera parte del proyecto de base de datos de estudiantes.

---

## Registro de Actividades

### Paso 1: Inicio del Terminal

1. **Acción**: Abre un nuevo terminal en tu entorno de desarrollo.
   - **Cómo hacerlo**:
     1. Haz clic en el menú "hamburger" en la parte superior izquierda de la pantalla.
     2. Ve a la sección "terminal" y selecciona "nuevo terminal".
   - **Comando Ejecutado**:
     ```bash
     echo hello SQL
     ```
   - **Resultado Esperado**: El terminal debería mostrar el mensaje `hello SQL`.

### Paso 2: Ingreso a PostgreSQL

1. **Acción**: Revisa los archivos `.csv` con información sobre los estudiantes de ciencias de la computación.
   - **Descripción**: Los archivos `.csv` contienen datos sobre los estudiantes. La primera fila de cada archivo tiene los títulos, y las filas restantes contienen los valores correspondientes a esos títulos.
2. **Acción**: Ingresar al terminal interactivo de PostgreSQL.
   - **Cómo hacerlo**:
     1. Abrir un nuevo terminal (si no está ya abierto).
     2. Ejecutar el siguiente comando para iniciar sesión en PostgreSQL:
        ```bash
        psql --username=freecodecamp --dbname=postgres
        ```
   - **Resultado Esperado**: Deberías ver el prompt de PostgreSQL listo para aceptar comandos SQL.

### Paso 3: Ver las Bases de Datos Existentes

1. **Acción**: Visualizar las bases de datos existentes utilizando el comando abreviado `\l`.
   - **Cómo hacerlo**:
     1. En el prompt de PostgreSQL, ejecuta el siguiente comando:
        ```psql
        \l
        ```
   - **Resultado Esperado**: Deberías ver una lista de todas las bases de datos actuales en el servidor PostgreSQL.

### Paso 4: Crear la Base de Datos de Estudiantes

1. **Acción**: Toda la información de los archivos CSV se almacenará en una sola base de datos. Crea una nueva base de datos llamada `students`.
   - **Cómo hacerlo**:
     1. En el prompt de PostgreSQL, ejecuta el siguiente comando:
        ```psql
        CREATE DATABASE students;
        ```
   - **Resultado Esperado**: La base de datos `students` debería ser creada exitosamente.

### Paso 5: Verificar la Creación de la Base de Datos

1. **Acción**: Verifica que la base de datos haya sido creada correctamente.
   - **Comando Ejecutado**:
     ```psql
     \l
     ```
   - **Resultado Esperado**: Deberías ver la base de datos `students` listada entre las bases de datos existentes.

### Paso 6: Conectar a la Nueva Base de Datos

1. **Acción**: Conéctate a la base de datos `students` para comenzar a agregar tablas.
   - **Comando**:
     ```psql
     \c students
     ```
   - **Resultado Esperado**: Deberías estar conectado a la base de datos `students`, lista para agregar tablas.

### Paso 7: CREAR TABLA 

Los archivos CSV contienen una serie de estudiantes con información sobre ellos, y algunos cursos y especialidades. Tendrás cuatro tablas: una para `students` y su información, una para cada especialidad `majors`, otra para cada curso `courses` y una última para mostrar qué cursos están incluidos en cada especialidad `majors_courses`. 

**Consejos**
- Utiliza las palabras clave `CREATE TABLE`.
- Debe haber paréntesis después del nombre de la tabla.
- He aquí un ejemplo: `CREATE TABLE <table_name>();`

1. **Acción**:
Escribe `CREATE TABLE students();` en el indicador psql.

Escribe `CREATE TABLE majors();` en el indicador psql.

Escribe `CREATE TABLE courses();` en el indicador psql.

Escribe `CREATE TABLE majors_courses();` en el indicador psql.


### Paso 8: VERIFICAR TABLAS

Utiliza el comando de atajo `\d` para visualizar tus tablas y asegurarte de que estás satisfecho con ellas.

**Consejos**
- Es el comando de atajo `\d`.
- Escribe `\d` en el indicador psql.


### Paso 9: CREAR COLUMNA 

Vamos a agregar columnas a la tabla `students` utilizando datos del archivo `students.csv`. Este archivo tiene cuatro campos, y agregaremos una columna para cada uno de esos campos, así como una columna ID.

**Consejos:**
- Utiliza la sentencia `ALTER TABLE` para agregar columnas a una tabla existente.
- Asegúrate de especificar el tipo de datos y cualquier restricción necesaria para cada columna.

 1. **Acción**: agregar `student_id` a la tabla `students`. Asigna a esta columna el tipo `SERIAL` para que se incremente automáticamente y conviértela en `PRIMARY KEY`.

`ALTER TABLE students ADD COLUMN student_id SERIAL PRIMARY KEY;`

2. **Acción**: Agregar columna first_name: Agrega una columna first_name a la tabla students. Asigna a esta columna el tipo VARCHAR(50) y dale la restricción NOT NULL.

`ALTER TABLE students ADD COLUMN first_name VARCHAR(50) NOT NULL;`

3. **Acción**: Agregar columna last_name: Agrega una columna last_name a la tabla students. Asigna a esta columna el mismo tipo de datos y longitud máxima que first_name y asegúrate de que tenga la restricción NOT NULL.

`ALTER TABLE students ADD COLUMN last_name VARCHAR(50) NOT NULL;`

4. **Acción**: Agregar columna major_id: Agrega una columna major_id a la tabla students. Asigna a esta columna el tipo de datos INT. Estableceremos la clave foránea más adelante.

`ALTER TABLE students ADD COLUMN major_id INT;`

5. **Acción**: Agregar columna gpa: Agrega una columna gpa a la tabla students. Los datos en el CSV muestran que son decimales con una longitud de 2 y 1 número a la derecha del decimal, así que asígnale un tipo de datos NUMERIC(2,1).

`ALTER TABLE students ADD COLUMN gpa NUMERIC(2,1);`

Este conjunto de instrucciones te guiará en la creación de todas las columnas necesarias para la tabla `students` a partir de los datos en `students.csv`.
Ahora vamos a agregar columnas. El archivo `students.csv` tiene cuatro campos; deberás crear una columna para cada uno de esos campos, así como una columna ID. 


### Paso 10: AÑADIR COLUMNAS A LA TABLA majors

Completa la tabla `majors`. 

1. **Acción**: Añade una columna `major_id` a esta tabla. Configúrala como un tipo `SERIAL` y hazla la PRIMARY KEY para esta tabla.

- Escribe `ALTER TABLE majors ADD COLUMN major_id SERIAL PRIMARY KEY;` en el indicador psql.

2. **Acción**: Añade una columna a la tabla `majors` llamada `major`. Configúrala como `VARCHAR` con una longitud máxima de 50 y dale la restricción `NOT NULL`.

- Escribe `ALTER TABLE majors ADD COLUMN major VARCHAR(50) NOT NULL;` en el indicador psql.

### Paso 11: ESTABLECER CLAVE FORÁNEA EN LA TABLA students

Configurar la columna `major_id` de la tabla `students` como una clave foránea que hace referencia a la columna `major_id` de la tabla `majors`.

1. **Acción**
- Aquí tienes un ejemplo de cómo hacerlo:
  ```psql
  ALTER TABLE students ADD FOREIGN KEY (major_id) REFERENCES majors (major_id);
  ```

### Paso 21: CREAR COLUMNA course_id

Agregue una columna course_id. Dale un tipo de SERIAL y conviértelo en la clave principal.

**Acción**
- Escriba en el indicador psql:
 ```psql
  ALTER TABLE courses ADD COLUMN course_id SERIAL PRIMARY KEY;
 ```


  
