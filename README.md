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

### Paso 7: CREAR TABLA `students`

Los archivos CSV contienen una serie de estudiantes con información sobre ellos, y algunos cursos y especialidades. Tendrás cuatro tablas: una para los estudiantes y su información, una para cada especialidad, otra para cada curso y una última para mostrar qué cursos están incluidos en cada especialidad. Primero, crea la tabla `students`.

**Consejos**
- Utiliza las palabras clave `CREATE TABLE`.
- Debe haber paréntesis después del nombre de la tabla.
- He aquí un ejemplo: `CREATE TABLE <table_name>();`

**Acción**
Escribe `CREATE TABLE students();` en el indicador psql.

### Pao 8: CREAR TABLA `majors`

La segunda tabla será para cada especialidad única que aparezca en los datos. Crea una tabla llamada `majors`.

**Acción**
Escribe `CREATE TABLE majors();` en el indicador psql.

### Paso 9: CREAR TABLA `courses`

La tercera tabla es para cada curso único en los datos. Crea otra tabla llamada `courses`.

**Acción**
Escribe `CREATE TABLE courses();` en el indicador psql.

### Paso 10: CREAR TABLA `majors_courses`

La tabla final será una tabla de unión para las especialidades y los cursos. Créala con el nombre `majors_courses`.

**Acción**
Escribe `CREATE TABLE majors_courses();` en el indicador psql.

### Paso 11: VERIFICAR TABLAS

Utiliza el comando de atajo `\d` para visualizar tus tablas y asegurarte de que estás satisfecho con ellas.

**Consejos**
- Es el comando de atajo `\d`.
- Escribe `\d` en el indicador psql.

### Paso 12: CREAR COLUMNA student_id

Ahora vamos a agregar columnas. El archivo `students.csv` tiene cuatro campos; deberás crear una columna para cada uno de esos campos, así como una columna ID. Agrega una columna a la tabla `students` llamada `student_id`. Asigna a esta columna el tipo `SERIAL` para que se incremente automáticamente y conviértela en `PRIMARY KEY`.

**Acción**
- Escribe `ALTER TABLE students ADD COLUMN student_id SERIAL PRIMARY KEY;` en el indicador psql.

### Paso 13: CREAR COLUMNA first_name

La primera columna en `students.csv` es `first_name`. Agrega una columna a la tabla `students` con ese nombre. Asigna a esta columna el tipo `VARCHAR(50)` y dale la restricción `NOT NULL`.

**Acción**
- Escribe `ALTER TABLE students ADD COLUMN first_name VARCHAR(50) NOT NULL;` en el indicador psql.

### Paso 14: CREAR COLUMNA last_name

La siguiente columna en los datos es `last_name`. Agrégala a la tabla `students`. Asigna a esta columna el mismo tipo de datos y longitud máxima que `first_name` y asegúrate de que tenga la restricción `NOT NULL`.

**Acción**
- Escribe `ALTER TABLE students ADD COLUMN last_name VARCHAR(50) NOT NULL;` en el indicador psql.

### Paso 15: CREAR COLUMNA major_id

La siguiente columna es para la especialidad. Dado que cada especialidad estará en otra tabla, esta columna será una clave foránea que la referenciará. Crea una columna en la tabla `students` llamada `major_id`, asígnale un tipo de datos `INT` por ahora. Regresaremos a establecer la clave foránea más adelante.

**Acción**
- Escribe `ALTER TABLE students ADD COLUMN major_id INT;` en el indicador psql.

### Paso 16: CREAR COLUMNA gpa

Crea la última columna, `gpa`. Los datos en el CSV muestran que son decimales con una longitud de 2 y 1 número a la derecha del decimal. Así que asígnale un tipo de datos `NUMERIC(2,1)`.

**Acción**
- Escribe `ALTER TABLE students ADD COLUMN gpa NUMERIC(2,1);` en el indicador psql.

### Paso 17: VISUALIZAR DETALLES DE LA TABLA students

Utiliza el comando de atajo para mostrar los detalles de la tabla `students`.

**Consejos**
- Es el comando de atajo `\d`.
- Escribe `\d students` en el indicador psql.

### Paso 18: AÑADIR COLUMNAS A LA TABLA majors

La clave foránea aún falta. Primero, completa la tabla `majors`. Añade una columna `major_id` a esta tabla. Configúrala como un tipo `SERIAL` y hazla la PRIMARY KEY para esta tabla.

**Acción**
- Escribe `ALTER TABLE majors ADD COLUMN major_id SERIAL PRIMARY KEY;` en el indicador psql.

### Paso 19: AÑADIR COLUMNA A LA TABLA majors

Esta tabla solo tendrá una columna adicional para el nombre de la especialidad. Añade una columna a la tabla `majors` llamada `major`. Configúrala como `VARCHAR` con una longitud máxima de 50 y dale la restricción `NOT NULL`.

**Acción**
- Escribe `ALTER TABLE majors ADD COLUMN major VARCHAR(50) NOT NULL;` en el indicador psql.

### Paso 20: ESTABLECER CLAVE FORÁNEA EN LA TABLA students

Configurar la columna `major_id` de la tabla `students` como una clave foránea que hace referencia a la columna `major_id` de la tabla `majors`.

**Acción**
- Aquí tienes un ejemplo de cómo hacerlo:
  ```sql
  ALTER TABLE students
  ADD FOREIGN KEY (major_id)
  REFERENCES majors (major_id);

### Paso 21: CREAR COLUMNA course_id

Agregue una columna course_id. Dale un tipo de SERIAL y conviértelo en la clave principal.

**Acción**
- Escriba en el indicador psql:
```sql
  ALTER TABLE courses
  ADD COLUMN course_id
  SERIAL PRIMARY KEY;
```


  
