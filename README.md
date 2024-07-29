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


### Paso 12: CREAR COLUMNA course_id

Agregue una columna course_id. Dale un tipo de SERIAL y conviértelo en la clave principal.

1. **Acción**
- Escriba en el indicador psql:
 ```psql
  ALTER TABLE courses ADD COLUMN course_id SERIAL PRIMARY KEY;
 ```


### Paso 13 Crear clave primaria compuesta

Puede crear una clave primaria compuesta que utilice más de una columna como un par único.

Ejemplo:
`ALTER TABLE <nombre_tabla> ADD PRIMARY KEY(<nombre_columna>, <nombre_columna>);`
1. **Acción:**
    ```psql
     ALTER TABLE majors_courses ADD PRIMARY KEY(major_id, course_id);
     ```
    

### Paso 14 INSERT EN majors

Sólo necesita el nombre de una especialización. La ID se agregará automáticamente. Agregue la primera especialización del archivo cursos.csv a la tabla de especialidades. Es un VARCHAR, así que asegúrese de poner el valor entre comillas simples. La especialidad es Administración de Bases de Datos.
Utilice las palabras clave `INSERT INTO` y `VALUES`

Ejemplo:
`INSERT INTO <nombre_tabla>(<nombre_columna>) VALUES(<valor>);`
  
   1. **Acción:**
      ```psql
      INSERT INTO majors(principales) VALUES('Administración de bases de datos');
      ```


### Paso 15 SELECT - FROM

Utilice las palabras clave SELECT y FROM con * para ver todas las columnas y asegurarse de que se hayan insertado correctamente.
  
   Ejemplo:
   `SELECT <columnas> FROM <nombre_tabla>;`
 
   1. **Acción:**
      ```psql
      SELECT * FROM majors;
      ```
      ```psql
      SELECT * FROM courses;
      ```
      ```psql
      SELECT * FROM majors_courses;
      ```
      ```psql
      SELECT * FROM students;
      ```


### Paso 16 touch insert_data.sh

Añadir el resto de la información de a una por vez sería tedioso. Para facilitar este proceso, te recomiendo dividir la terminal. Puedes hacerlo siguiendo estos pasos,
haz clic en el menú de "hamburguesa" en la parte superior izquierda de la ventana => ve al menú "Terminal" => haz clic en "Dividir terminal".

1. **Acción**:

 - Usa el comando `touch` para crear un archivo llamado `insert_data.sh`
 
 - Asegúrate de estar en la `project` carpeta primero.

 - Puedes llegar ingresando `cd ~/project` la terminal.


### Paso 17 chmod +x insert_data.sh

Debes tener dos terminales abiertas. Una conectada a PostgreSQL y otra para ingresar a la terminal de comandos. En la terminal de comandos, usa el `chmod` comando con el `+x` indicador para otorgarte nuevos permisos de ejecución de scripts.

1. **Acción**:

- Escribe `chmod +x insert_data.sh` en la terminal y pulsa enter.
     
- Asegúrese de que sea la terminal normal y no la psql.

- Puede volver a iniciar sesión en psql conpsql `--username=freecodecamp --dbname=students`
  

### Paso 18 Add shebang

Abra el archivo nuevo y agregue un "shebang" que use `bash ` en la parte superior. Se verá así: `#!/bin/bash`.

1. **Acción**:

- Añade el texto `#!/bin/bash` a tu `insert_data.sh` archivo.


### Paso 19 Agregar Comentario

Debajo de eso, agregue un comentario de una sola línea con el texto, `Script to insert data from courses.csv and students.csv into students database`.

1. **Acción**:

- Un comentario se vería así: `# <comment>`.

- Añade `# Script to insert data from courses.csv and students.csv into students database` a continuación el "shebang" en tu `insert_data.sh` archivo.


### Paso 20 Agregar cat courses.csv

`cat` es un comando de terminal para imprimir el contenido de un archivo. Debes agregar toda la información del archivo `courses.csv` ya que necesitas el `major_id ` para insertar la información de los estudiantes.

1. **Acción**:

-  Añade `cat courses.csv` a tu `insert_data.sh` archivo debajo tu comentario.


### Paso 21 ./insertar_datos.sh

1. **Acción**:

- Escribe `./insert_data.sh` en la terminal de comandos y pulsa enter.

- Asegúrate de estar en la `project` carpeta primero.



### Paso 22 Agregue while read

En lugar de imprimir el contenido, puede redirigir esa salida en un bucle while para poder recorrer las filas una a la vez.
Cada nueva línea se leerá en las variables `MAJOR` y `COURSE`, use `echo` para imprimir la variable `MAJOR`.
  
   1. **Acción:**

      El bucle completo debería verse así:
    
      ```sh
      cat courses.csv | while read MAJOR COURSE
      do
        echo $MAJOR
      done
      ```


### Paso 23 Declarar -p IFS y Añadir IFS

La variable `MAJOR` solo está capturando la primera palabra de cada línea. Esto se debe a la variable predeterminada `IFS` en bash. `IFS` significa "Internal Field Separator" (Separador de Campos Interno) y define cómo se separan los campos en bash. Para ver el valor actual de IFS, puedes usar el siguiente comando en la terminal:

 1. **Acción**:

  - Ingresa `declare -p IFS` en la terminal.

Entre los comandos `while`y `read`, establezca el `IFS` en una coma de la siguiente manera:`IFS=","`
 
2. **Acción**:

```sh
cat courses.csv | while IFS="," read MAJOR COURSE
do
  echo $MAJOR
done
```


### Paso 24 Agregar # Comentario

Ayuda planificar lo que quieres que suceda. Para cada bucle, deberás añadir la especialidad `major` a la base de datos si aún no está allí. Lo mismo para el curso. Luego, añade una fila a la tabla `majors_courses`. Agrega estos comentarios de una línea en tu bucle en el siguiente orden: `get major_id`, `if not found`, `insert major`, `get new major_id`, `get course_id`, `if not found`, `insert course`, `get new course_id`, `insert into majors_courses`.

1. **Acción**:

- Aquí tienes un ejemplo de un comentario de una línea: `# <comentario>`.

- Agrega los nueve comentarios de una línea sugeridos, cada uno en su propia línea, en el orden dado. Debería verse así:

```sh
do
  # get major_id

  # if not found

  # insert major

  # get new major_id

  # get course_id

  # if not found

  # insert course

  # get new course_id

  # insert into majors_courses

done
```


### Paso 25 Añadir Variable PSQL

Usaste el comando `psql` para iniciar sesión e interactuar con la base de datos. También puedes usarlo para ejecutar un solo comando y salir. Por encima de tu bucle, añade una variable `PSQL` que se vea así:

 ```sh
PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
```

1. **Acción**:

- Añade la variable sugerida entre tu primer comentario y el bucle.

- La sección sugerida debería verse así:

 ```sh
PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
```


### Paso 26 Agrega MAJOR_ID
puedes consultar tu base de datos usando la variable `PSQL` de esta manera: `$($PSQL "<query_here>")`. El código entre paréntesis se ejecutará en un subshell, que es un proceso bash separado. Debajo del comentario `get major_id` en tu bucle, crea una variable `MAJOR_ID`. Establécela igual al resultado de una consulta que obtenga el `major_id` del `MAJOR` actual en el bucle. Asegúrate de poner tu variable `MAJOR` entre comillas simples.
 1. **Acción**:
    ejemplo: `MAJOR_ID=$($PSQL "<query_here>")`,
     ```sh
     MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
     ```


### Paso 27 Agrega echo MAJOR_ID
Debajo de la variable que acabas de crear, usa echo para imprimirla y así poder ver su valor cuando ejecutes el script.
   1. **Acción**:
      Agrega `echo $MAJOR_ID` debajo de la variable MAJOR_ID que creaste


### Paso 28 Agregue if -z MAJOR_ID
Debajo de su primer comentario `if not found`, agregue una condición `if` que verifique si la variable `MAJOR_ID` está vacía. Puede hacerlo con esta prueba: `[[ -z $MAJOR_ID ]]`. Coloque los dos comentarios siguientes en el área de declaraciones del `if`.
   1. **Acción**:
      Ejemplo:
      if CONDITION
      then
      STATEMENTS
      fi
      ```sh
      if [[ -z $MAJOR_ID ]]
      then
      # insert major
      # get new major_id
      fi
      ```

### Paso 29 Agregar INSERT_MAJOR_RESULT

El bucle entrará en esta condición siempre que no se encuentre una especialidad (major). En este caso, debes insertar la especialidad y luego obtener el nuevo ID. Necesitarás el ID para insertar datos en la tabla majors_courses más adelante.

Debajo de tu comentario de "insertar especialidad", crea una variable llamada INSERT_MAJOR_RESULT. Asigna a esta variable una consulta que inserte la especialidad actual en la base de datos. No olvides usar comillas simples alrededor del valor.

**Ejemplo**:

- Aquí tienes un ejemplo de cómo consultar la base de datos:

```sh 
   INSERT_MAJOR_RESULT=$($PSQL "<query_here>")
```

1. **Acción**:

Así es como se ve la consulta completa:

```sh
INSERT INTO majors(major) VALUES('$MAJOR')
```

- Así es como debería verse toda la línea:

```sh
INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
```

2. **Acción**:

- Agrega `echo $INSERT_MAJOR_RESULT` justo debajo de donde lo creaste.


### Paso 30 cp courses.csv

Cree algunos datos de prueba. En la terminal, usa el comando `cp` para copiar el archivo courses.csv a un nuevo archivo llamado `courses_test.csv`.

- Aquí tienes un ejemplo: `cp <filename> <new_name>`.

1. **Acción**:

- Escribe `cp courses.csv courses_test.csv` en la terminal y presiona enter.

- Asegúrate de estar utilizando la terminal bash y no la de psql.


2. **Acción**:

- Elimina todas las líneas excepto las primeras cinco del archivo `courses_test.csv`.

- El `ourses_test.csv` carchivo debería verse así:

```sh

major,course
Database Administration,Data Structures and Algorithms
Web Development,Web Programming
Database Administration,Database Systems
Data Science,Data Structures and Algorithms
```


### Paso 31 Cambia a cat courses_test.csv

En el script `insert_data.sh`, cambia tu comando `cat` para que itere a través del archivo de prueba en lugar del archivo completo.

1. **Acción**:

- La línea sugerida debería verse así:

```sh

cat courses_test.csv | while IFS="," read MAJOR COURSE
```

### Paso 32 Elimina echo MAJOR_ID

Parece que encontró un ID que ya estaba en la base de datos dos veces e insertó tres nuevos elementos en la base de datos. Ya no necesitas imprimir el ID, así que elimina la línea `echo $MAJOR_ID`.

1. **Acción**:

- Elimina la línea `echo $MAJOR_ID`.


### Paso 33 SELECT * FROM majors

En el prompt de `psql`, utiliza SELECT para ver todos los datos de la tabla `majors` y así comprobar qué agregó el script.

1. **Acción**:

- Escribe `SELECT * FROM majors;` en el prompt de `psql`.


### Paso 34 TRUNCATE majors

Puedes usar TRUNCATE para eliminar todos los datos de una tabla. En el prompt de `psql`, intenta eliminar todos los datos de la tabla majors ingresando `TRUNCATE majors;`.

1. **Acción**:

- Escribe `TRUNCATE majors;` en el prompt de `psql`.


### Paso 35 TRUNCATE majors, students, majors_courses

Dice que "no se puede truncar una tabla referenciada en una restricción de clave externa". Las tablas `students` y `majors_courses` utilizan el `major_id` de `majors` como clave externa. Por lo tanto, si deseas eliminar los datos de `majors`, debes eliminar los datos de esas dos tablas al mismo tiempo. Usa `TRUNCATE` para eliminar los datos de las tres tablas. Separa las tablas con comas.

1. **Acción**:

- Ingresa `TRUNCATE majors, students, majors_courses;` en el prompt de `psql`.

2. **Acción**:

- Mira todos los datos en la tabla `majors`, `students`, `majors_courses` y `courses` para asegurarte de que estén vacías.

-Ejemplo para cada tabla:

-  `SELECT * FROM majors;` en el prompt de psql.


### Paso 36 Agregar if major

No querrás agregar la primera línea del archivo CSV a la base de datos, ya que solo contiene títulos. En tu script, añade una condición `if` al principio de tu bucle que verifique si `$MAJOR != major`. Coloca todo el código y los comentarios existentes en tu bucle dentro del área de las declaraciones del `if` para que solo se ejecute si no es la primera línea.

1. **Acción**:
   
- Aquí tienes un ejemplo de una condición `if`:

```sh
if [[ CONDITION ]]
then
  STATEMENTS
fi
```

- Tu área del bucle debería verse así:

```sh
do
  if [[ $MAJOR != major ]]
  then
    # obtener major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

    # si no se encuentra
    if [[ -z $MAJOR_ID ]]
    then
      # insertar major
      INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
      echo $INSERT_MAJOR_RESULT

      # obtener nuevo major_id

    fi

    # obtener course_id

    # si no se encuentra

    # insertar course

    # obtener nuevo course_id

    # insertar en majors_courses

  fi
done
```


### Paso 37 Elimina echo INSERT_MAJOR_RESULT

Elimina la línea donde imprimes `INSERT_MAJOR_RESULT`.

1. **Acción**:

Elimina la línea `echo $INSERT_MAJOR_RESULT`.


### Paso 38 Añadir if INSERT_MAJOR_RESULT

Para que sea más informativo debajo de tu variable `INSERT_MAJOR_RESULT`, añade una declaración `if` que verifique si la variable es igual a `INSERT 0 1`, que era lo que estaba imprimiendo. Usa echo para imprimir `"Inserted into majors, $MAJOR"` en el área de declaraciones del `if`.

1. **Acción**:

- Todo debería verse así:

```sh
if [[ $INSERT_MAJOR_RESULT == "INSERT 0 1" ]]
then
  echo "Inserted into majors, $MAJOR"
fi
```


### Paso 39 Añadir MAJOR_ID, COURSE_ID y if -z COURSE_ID

Debajo de tu comentario `get new major_id`, establece la variable `MAJOR_ID`.

1. **Acción**:

- Así debería verse toda la línea: `MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")`

Asegúrate de que esté en el área de declaraciones del `if [[ -z $MAJOR_ID ]]`.

Debajo de tu comentario `get course_id`, añade una variable `COURSE_ID` que obtenga el `course_id` de la base de datos. Recuerda que tu variable `COURSE` tendrá el curso actual en el bucle.

2. **Acción**:

- Así debería verse toda la línea: `COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")`.

Debajo del segundo comentario `if not found`, añade una declaración `if` que verifique si la consulta está vacía para que puedas insertar el curso si es necesario. Coloca los comentarios existentes `insert course` y `get new course_id` en el área de declaraciones del `if`.

3. **Acción**:

- Aquí es cómo debería verse:

```sh

if [[ -z $COURSE_ID ]]
then
  # insertar curso

  # obtener nuevo course_id

fi
```


### Paso 40 Añadir INSERT_COURSE_RESULT y if INSERT_COURSE_RESULT

Debajo del comentario `insert course`, crea una variable `INSERT_COURSE_RESULT` que inserte el curso en la base de datos.

1. **Acción**:

- Así es cómo debería verse toda la línea: `INSERT_COURSE_RESULT=$($PSQL "INSERT INTO courses(course) VALUES('$COURSE')")`.

Debajo de la variable que acabas de crear, añade una condición `if` que verifique si es así e imprime `Inserted into courses, $COURSE` usando `echo` en su área de declaraciones.

2. **Acción**:

- Todo debería verse así:

```sh

if [[ $INSERT_COURSE_RESULT == "INSERT 0 1" ]]
then
  echo "Inserted into courses, $COURSE"
fi
```


### Paso 41 Agregue echo TRUNCATE tables

En lugar de eliminar manualmente los datos cada vez que desee ejecutar el script, agregue el comando para que lo haga por usted. Cerca de la parte superior del archivo, debajo de la variable `PSQL`, use `echo` para consultar la base de datos. En la consulta, quite las filas de las cuatro tablas en este orden: `students`, `majors`, `courses`, `majors_courses`.
  
   1. **Acción**:
      Toda la línea debería verse así:
      ```sh
      echo $($PSQL "TRUNCATE students, majors, courses, majors_courses")
      ```


### Paso 42 Agrega COURSE_ID, INSERT_MAJORS_COURSES_RESULT, if INSERT_MAJORS_COURSES_RESULT

Debajo del comentario para obtener el nuevo `course_id`, establece el `COURSE_ID` en el `course_id` recién insertado.
  
   1. **Acción**:

       Así es como debería verse toda la línea, Asegúrese de que esté en el área de declaraciones `if [[ -z $COURSE_ID ]]`:
      ```sh
      COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")
      ```
  
   2. **Acción**:

       Debajo del comentario de inserción en cursos de `majors_courses`, crea una variable `INSERT_MAJORS_COURSES_RESULT`. Úsala junto con las variables `MAJOR_ID` y `COURSE_ID` que creaste para insertar una fila en la tabla `majors_courses`. Asegúrate de que la consulta tenga primero la columna `major_id`. Además, no necesitarás comillas alrededor de los valores de los identificadores.
    
      Así es como debería verse toda la línea:
      ```sh
      INSERT_MAJORS_COURSES_RESULT=$($PSQL "INSERT INTO majors_courses(major_id, course_id) VALUES($MAJOR_ID, $COURSE_ID)")
      ```
   
   3. **Acción**:
      Debajo de la variable que acaba de crear, agregue una condición `if` que verifique si es igual a `INSERT 0 1` como las demás. En su área de declaraciones, use `echo` para imprimir `Inserted into majors_courses, $MAJOR : $COURSE`.
      Todo debería verse así:
      ```sh
      if [[ $INSERT_MAJORS_COURSES_RESULT == "INSERT 0 1" ]]
         then
         echo "Inserted into majors_courses, $MAJOR : $COURSE"
         fi
      ```


### Paso 43 cp students.csv, cat students_test.csv

A continuación, debes agregar todo lo del archivo `students.csv`. Crea algunos datos de prueba nuevamente. En la terminal, usa el comando `copy` para copiar `students.csv` en un archivo llamado `students_test.csv`.

   1. **Acción**:
      Ingresa `cp students.csv students_test.csv` en la terminal
      
   2. **Acción**:

       En el archivo `students_test.csv`, elimina todo excepto las primeras cinco líneas como lo hiciste para el otro archivo de prueba. Asegúrate de que haya una línea vacía en la parte inferior nuevamente.
      
   3. **Acción**:

      Debajo del bucle existente, use `cat` para imprimir su nuevo archivo de prueba. Convierte los resultados en un bucle `while`, configurando `IFS` en una coma nuevamente y luego usa `read` para crear las variables `FIRST`, `LAST`, `MAJOR` y ``GPA a partir de los datos. En el bucle, usa `echo` para imprimir la variable `FIRST`.
      Así es como se ve:
      ```sh
      cat students_test.csv | while IFS="," read FIRST LAST MAJOR GPA
      do
         echo $FIRST
      done
      ```
 
   4. **Acción**:
      Borra la línea echo $FIRST


### Paso 44 Agrega if first_name y comentarios

Agrega una condición `if` al bucle que verifique si la variable `FIRST` no es igual a `first_name` para que no haga nada en la primera línea del archivo. Agregue cuatro comentarios de una sola línea en su bucle; `get major_id`, `if not found`, `set to null`, e `insert student` en ese orden.

   1. **Acción**:
      
      Su segundo bucle debería verse así:
      ```sh
      cat students_test.csv | while IFS="," read FIRST LAST MAJOR GPA
      do
         if [[ $FIRST != "first_name" ]]
         then
         # get major_id
         # if not found
         # set to null
         # insert student
         fi
      done
      ```


### Paso 45 Agregue MAJOR_ID, echo MAJOR_ID, if -z MAJOR_ID, establezca MAJOR_ID en null y Elimine echo MAJOR_ID

Debajo del nuevo comentario `get major_id`, configure la variable `MAJOR_ID` en una consulta que obtenga el `major_id` de la especialidad del estudiante actual.

   1. **Acción**:
      Así es como debería verse toda la línea:
      ```sh
      MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
      ```
      
   2. **Acción**:
      Agregue `echo $MAJOR_ID` debajo de la variable `MAJOR_ID` que acaba de crear.
      
   3. **Acción**:

      Debajo del comentario `if not found`, agregue un `if` que verifique si la variable está vacía. Coloque el comentario `set to null` en su área de declaraciones.
      Debería verse así:
      ```sh
      if [[ -z $MAJOR_ID ]]
      then
         # set to null
      fi
      ```
   
   4. **Acción**:

      Debajo del comentario `set to null`, establezca la variable `MAJOR_ID` en `null` para que pueda usarla para insertar los datos.
      Debería verse así:
      ```sh
      if [[ -z $MAJOR_ID ]]
      then
         # set to null
         MAJOR_ID=null
      fi
      ```
  
   5. **Acción**:
      Elimine la línea `echo $MAJOR_ID` del archivo.


### Paso 46 Agregue INSERT_STUDENT_RESULT, if INSERT_STUDENT_RESULT

Deberá configurar las cuatro columnas al agregar la información del estudiante. Todas excepto `student_id`. Debajo del comentario de inserción del estudiante, cree una variable `INSERT_STUDENT_RESULT` que agregue al estudiante a la base de datos. Agregue las columnas en el orden en que aparecen en los datos y asegúrese de poner solo las dos columnas `VARCHAR` entre comillas simples.

   1. **Acción**:
      Así es como debería verse toda la línea:
      ```sh
      INSERT_STUDENT_RESULT=$($PSQL "INSERT INTO students(first_name, apellido, id_major, gpa) VALUES('$FIRST', '$LAST', $MAJOR_ID, $GPA)")
      ```
   2. **Acción**:

      Debajo de la variable que acaba de crear, agregue una declaración `if` que verifique si es igual a `INSERT 0 1` como las demás. Si lo es, use `echo` para imprimir `Inserted into students, <first_name> <last_name>`.
      Todo debería verse así:
      ```sh
      if [[ $INSERT_STUDENT_RESULT == "INSERT 0 1" ]]
      then
         echo "Inserted into students, $FIRST $LAST"
      fi
      ```
  
   3. **Acción**:

       Vea todos los datos en la tabla de estudiantes para asegurarse de que coincidan con el archivo CSV.
      Ingrese `SELECT * FROM students;` en el indicador de psql


### Paso 47 Cambiar a cat courses.csv y cat students.csv

Agregó todos los estudiantes de los datos de la prueba. Es hora de probarlo con los archivos originales. Cambie la línea `cat courses_test.csv` y `cat students_test.csv` para usar el archivo original nuevamente.

   1. **Acción**:

       Cambie `cat courses_test.csv` a `cat courses.csv`
      La línea sugerida debería verse así: `cat courses.csv | while IFS="," read MAJOR COURSE`
      
   3. **Acción**:

      Cambie `cat students_test.csv` a `cat students.csv`
      La línea sugerida debería verse así: `cat students.csv | mientras IFS="," leer PRIMERO ÚLTIMO PROMEDIO DE CALIDAD`
      
   5. **Acción**:

       Ejecute el script y vea si funciona. Escriba `./insert_data.sh` en la terminal bash y presione enter.
      Después de ejecutar el script, las tablas deberían tener esta cantidad de filas: `majors` tiene 7, `courses` tiene 17, `majors_courses` tiene 28 y `students` debería tener 31.


### Paso 48 SELECT * FROM students, SELECT * FROM majors, SELECT * FROM courses, SELECT * FROM majors_courses

Vea todos los datos en la tabla `students`, `majors`, `courses` y `majors_courses` para ver con qué terminó.

   1. **Acción**:
      
      Ingrese  en el indicador de psql
      `SELECT * FROM students;`
      `SELECT * FROM majors;`
      `SELECT * FROM courses;`
      `SELECT * FROM majors_courses;`


### Paso 49 ls, rm students_test.csv, rm courses_test.csv

Ya no necesitas tus archivos de prueba. En la terminal, usa el comando `list` para verificar qué archivos hay en la carpeta de tu proyecto.

   1. **Acción**:

       Ingresa ls en la terminal
   
   2. **Acción**:

      Utilice el comando `remove` (`rm`) para eliminar el archivo `students_test.csv` y `courses_test.csv`.
      Introduzca `rm students_test.csv`
      Introduzca `rm courses_test.csv` en la terminal
  
   3. **Acción**:

       Vuelva a enumerar el contenido de la carpeta para asegurarse de que no haya más contenido. Introduzca `ls` en la terminal.


### Paso 49 pg_dump --help, dump database

La base de datos está terminada por ahora. Lo último que vas a hacer es crear un "volcado" de la base de datos. El comando `pg_dump` puede hacerlo por ti. Usa el indicador `--help` con el comando para ver lo que puede hacer.

- Ingresa `pg_dump --help` en la terminal bash

- Presiona enter hasta que hayas visto todo el manual

Este es el último paso.

- Ingresa `pg_dump --clean --create --inserts --username=freecodecamp students > students.sql` en la terminal para volcar la base de datos en un archivo `students.sql`. Guardará todos los comandos necesarios para reconstruirla. Echa un vistazo rápido al archivo cuando hayas terminado.



## Archivo insert_data.sh

```sh
#!/bin/bash

# Script to insert data from courses.csv and students.csv into students database

PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"
echo $($PSQL "TRUNCATE students, majors, courses, majors_courses")

cat courses.csv | while IFS="," read MAJOR COURSE
do
  if [[ $MAJOR != "major" ]]
  then
    # get major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")

    # if not found
    if [[ -z $MAJOR_ID ]]
    then
      # insert major
      INSERT_MAJOR_RESULT=$($PSQL "INSERT INTO majors(major) VALUES('$MAJOR')")
      if [[ $INSERT_MAJOR_RESULT == "INSERT 0 1" ]]
      then
        echo Inserted into majors, $MAJOR
      fi

      # get new major_id
      MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'")
    fi

    # get course_id
    COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")

    # if not found
    if [[ -z $COURSE_ID ]]
    then
      # insert course
      INSERT_COURSE_RESULT=$($PSQL "INSERT INTO courses(course) VALUES('$COURSE')")
      if [[ $INSERT_COURSE_RESULT == "INSERT 0 1" ]]
      then
        echo Inserted into courses, $COURSE
      fi

      # get new course_id
      COURSE_ID=$($PSQL "SELECT course_id FROM courses WHERE course='$COURSE'")
    fi

    # insert into majors_courses
    INSERT_MAJORS_COURSES_RESULT=$($PSQL "INSERT INTO majors_courses(major_id, course_id) VALUES($MAJOR_ID, $COURSE_ID)")
    if [[ $INSERT_MAJORS_COURSES_RESULT == "INSERT 0 1" ]]
    then
      echo Inserted into majors_courses, $MAJOR : $COURSE
    fi
  fi
done

cat students.csv | while IFS="," read FIRST LAST MAJOR GPA
do
  if [[ $FIRST != "first_name" ]]
  then
    # get major_id
    MAJOR_ID=$($PSQL "SELECT major_id FROM majors WHERE major='$MAJOR'") 

    # if not found
    if [[ -z $MAJOR_ID ]]
    then
      # set to null
      MAJOR_ID=null
    fi

    # insert student
    INSERT_STUDENT_RESULT=$($PSQL "INSERT INTO students(first_name, last_name, major_id, gpa) VALUES('$FIRST', '$LAST', $MAJOR_ID, $GPA)")
    if [[ $INSERT_STUDENT_RESULT == "INSERT 0 1" ]]
    then
      echo Inserted into students, $FIRST $LAST
    fi
  fi
done

```
