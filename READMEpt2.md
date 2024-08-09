# Student Database

## Learn SQL by Building a Student Database: Part 2

Este documento proporciona un registro detallado de las actividades realizadas y los comandos ejecutados durante la segunda parte del proyecto de base de datos de estudiantes.

---

## Registro de Actividades

### Paso 1 Iniciar el Terminal y Login en psql

Primero, abre el terminal haciendo clic en el menú "hamburguesa" , ve a la sección "terminal" y selecciona "new terminal". 
Una vez abierto, escribe echo hello SQL y presiona enter. Luego, para iniciar sesión en psql, escribe `psql --username=freecodecamp --dbname=postgres` en el terminal y presiona enter para acceder a la base de datos que creaste en la Parte 1 del tutorial.


### Paso 2 Reconstruir la base de datos

Tu base de datos no está aquí. Puedes usar el archivo `.sql` que creaste al final de la Parte 1 para reconstruirla. Divide el terminal, una vez hecho esto, ingresa `psql -U postgres < students.sql` para reconstruir la base de datos.


### Paso 3 Shortcut Command

1. **Acción**:

- Escriba `\l` en el indicador psql y presione Enter.
- Escriba `\c students` en el indicador psql para conectarse a la base de datos y presione Enter.
- Escriba `\d` en el indicador psql para visulizar las tablas y presione Enter.
- Escriba `\d students` en el indicador psql para ver los detalles de la tabla y presione Enter.


### Paso 4 SELECT * FROM students

Asegúrate de que todos los datos estén en la tabla también.

1. **Acción**:

- Escribe `SELECT * FROM students;` en el prompt de psql.


### Paso 5 touch student_info.sh

Usa touch en el terminal bash para crear `student_info.sh`. Vas a hacer un script para imprimir información sobre tus estudiantes.

1. **Acción**:

- Ingresa `touch student_info.sh` en el terminal.
- Usa el terminal bash, no el de psql.


### Paso 6 chmod +x student_info.sh

Otorgar permisos al nuevo archivo.

1. **Acción**:

- Aquí tienes un ejemplo: `chmod +x <filename>`.

- Escribe `chmod +x student_info.sh` en el terminal y presiona enter.


### Paso 7 Añade un shebang 

Añade un shebang que use bash al principio de tu nuevo script.

1. **Acción**:

- El shebang que necesitas es #!/bin/bash.

- Añade #!/bin/bash al archivo student_info.sh.

Añade un comentario.

2. **Acción**:

- Añade `# Info about my computer science students from students database` debajo del "shebang" en tu archivo `student_info.sh`.


### Paso 8 Agregue título echo

Añade un `echo` para el título. En el nuevo script, usa echo para imprimir `~~ My Computer Science Students ~~`. Usa el flag `-e ` para poner una nueva línea al principio y al final del texto.
El carácter de nueva línea es `\n`.

- Aquí tienes un ejemplo: echo -e "\n<texto>\n".

1. **Acción**:

- Añade `echo -e "\n~~ My Computer Science Students ~~\n"` debajo del comentario en tu archivo `student_info.sh`.


### Paso 9 ./student_info.sh

Ejecuta el script `student_info.sh` para asegurarte de que funciona correctamente.

1. **Acción**:

- Escribe `./student_info.sh` en la terminal y presiona Enter.


### Paso 10 Añadir Variable PSQL

Querrás consultar la base de datos nuevamente para obtener información sobre los estudiantes que mostrarás. Añade la misma variable PSQL que usas en tu script `insert_data.sh`. 

1. **Acción**:
   
- Debería verse así: `PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"`.


### Paso 11 Agregar echo para estudiantes con 4.0

Debajo de la variable PSQL que acabas de agregar, utiliza `echo` para imprimir `First name, last name, and GPA of students with a 4.0 GPA:`. Usa el flag `-e` para añadir una nueva línea al principio de la frase.

1. **Acción**:

- Escribe:

```sh 
echo -e "\nFirst name, last name, and GPA of students with a 4.0 GPA:"
```


### Paso 12 PSQL Consultas

SQL significa "Structured Query Language" (Lenguaje de Consulta Estructurado). Es el lenguaje que has estado usando para gestionar tus bases de datos relacionales. 
En el prompt de `psql`, visualiza todos los datos en la tabla students como lo has hecho muchas veces:

1. **Acción**:

- Ingresa `SELECT * FROM students;` en el prompt de psql.

Para ver solo una columna específica de una tabla:

2. **Acción**:

- Ingresa `SELECT first_name FROM students;` en el prompt de psql.

Para devolver múltiples columnas, sepáralas con comas en tu consulta.

3. **Acción**:

- Ingresa `SELECT first_name, last_name, gpa FROM students;` en el prompt de psql.

Para devolver solo las filas que cumplan con una condición específica, agrega ` WHERE <condición>` a tu consulta:

4. **Acción**:

- Usa `WHERE gpa < 2.5`.

Para mostrar filas donde el `gpa` sea mayor o igual a un valor específico, usa el operador `>=`:

5. **Acción**:

- Usa `WHERE gpa >= 3.8`.

Para devolver filas donde el `gpa` no sea igual a un valor específico, usa el operador `!=`:

6. **Acción**:

- Ingresa `SELECT first_name, last_name, gpa FROM students WHERE gpa != 4.0;` en el prompt de psql.


### Paso 13 Añadir echo del resultado de la consulta

En tu archivo `student_info.sh`, añade un comando echo al final que imprima lo que la frase anterior solicita. Coloca comillas dobles alrededor de esto de la siguiente manera: `echo "$($PSQL "<consulta_aquí>")"`. Esto hará que la salida no esté toda en una sola línea.

1. **Acción**:

- Añade `echo "$($PSQL "<consulta_aquí>")" al final del archivo student_info.sh`.

- Añade `echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE gpa = 4.0")"` al final del archivo `student_info.sh`.

2. **Acción**:

- Ejecutar el script `./student_info.sh` en la terminal de comandos.


### Paso 14 Añadir echo courses before D

Añade otra declaración `echo` al final del script.  Haz que imprima `All course names whose first letter is before 'D' in the alphabet:`.  Pon un salto de línea delante de esta frase, como en la primera oración.

1. **Acción**:

- Al final del `student_info.sh` archivo, agregue lo siguiente:

```sh
echo -e "\nAll course names whose first letter is before 'D' in the alphabet:"
```


### Paso 15 PSQL Consultas

Practica primero.

Para visualizar todos los datos en la tabla majors:

1. **Acción**:

- `SELECT * FROM majors;`.

Usa el = para ver todos los majors nombrados Game Design. La condición que necesitas es `major = 'Game Design'`:

2. **Acción**:

- `Ingresa SELECT * FROM majors WHERE major = 'Game Design';`

Para visualizar todas las filas que no sean iguales a Game Design. La condición que necesitas es `major != 'Game Design'`:

3. **Acción**:

- Ingresa `SELECT * FROM majors WHERE major != 'Game Design';`.

Para ver las especialidades que vienen después alfabéticamente. La condición que necesitas es `major > 'Game Design'`:

4. **Acción**:

- Ingresa `SELECT * FROM majors WHERE major > 'Game Design';`.

Game Design no se incluyó en los resultados porque no es > 'Game Design'. Inténtalo con el operador de mayor o igual que. La condición que necesitas es `major >= 'Game Design'`:

5. **Acción**:

- Ingresa `SELECT * FROM majors WHERE major >= 'Game Design';`

Ahora, ve los majors que vienen antes de G. La condición que necesitas es `major < 'G'`:

6. **Acción**:

- Ingresa `SELECT * FROM majors WHERE major < 'G';`.


### Paso 16 Agregar resultado de consulta con echo

En el script, agrega un `echo` al final para imprimir la información sugerida como lo hiciste antes. Asegúrate de usar comillas dobles donde sea necesario.

1. **Acción**:

- Agregar al final del archivo `student_info.sh`:

```sh
echo "$($PSQL "SELECT course FROM courses WHERE course < 'D'")"
```

2. **Acción**:

- Ejecuta el script `student_info.sh` en la terminal de comandos.


### Paso 17  Agregar echo 

Agrega otra oración como las anteriores que diga: `First name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:`

1. **Acción**:

- Al final del archivo `student_info.sh`, agrega esto:

```sh
echo -e "\nFirst name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:"
```


### Paso 18 PSQL Consultas

Para ver todos los datos en la tabla de estudiantes. Usa las palabras clave `SELECT` y `FROM` con `*` para ver todos los datos.

1. **Acción**:

- Ingresa `SELECT * FROM students;`.

Devuelve las filas de los estudiantes cuyo apellido esté antes de la M en el alfabeto. La condición que es `last_name < 'M'`:

2. **Acción**:

- Ingresa `SELECT * FROM students WHERE last_name < 'M';`.

Puedes usar múltiples condiciones después de `WHERE` con `AND` u `OR`, entre otros. Solo agrega la palabra clave y otra condición:

3. **Acción**:

- Ingresa `SELECT * FROM students WHERE last_name < 'M' OR gpa = 3.9;`

Ingresa el comando anterior, pero usa AND para ver solo estudiantes que cumplan ambas condiciones:

4. **Acción**:

- Ingresa `SELECT * FROM students WHERE last_name < 'M' AND gpa = 3.9;`.

Ingresa el comando anterior, pero agrega una tercera condición de `OR gpa < 2.3`:

5. **Acción**:

- Ingresa `SELECT * FROM students WHERE last_name < 'M' AND gpa = 3.9 OR gpa < 2.3;`.

Puedes agrupar condiciones juntas con paréntesis así: `WHERE <condition_1> AND (<condition_2> OR <condition_2>)`. Esto solo devolvería filas donde `<condition_1> ` es verdadera y una de las otras también es verdadera. Ve a los estudiantes cuyo apellido es antes de la M que tienen un `GPA de 3.9 o menor a 2.3`:

6. **Acción**:

- Ingresa `SELECT * FROM students WHERE last_name < 'M' AND (gpa = 3.9 OR gpa < 2.3);`.


### Paso 19 Agrega resultado de la consulta con echo

Dos estudiantes cumplen con esas condiciones. Regresa al archivo de información de los estudiantes y agrega un comando echo al final para imprimir las filas sugeridas. Agrega `echo "$($PSQL "<query_here>")"` al final del archivo `student_info.sh`, excepto con la consulta correcta.

1. **Acción**: 

- Agrega:

```sh
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE last_name >= 'R' AND (gpa > 3.8 OR gpa < 2.0)")"
```

2. **Acción**:

- Ejecuta el script `student_info.sh` en la terminal de comandos.


### Paso 20 Agrega echo

Agrega otro comando `echo`, como los anteriores, con una oración que diga: `Last name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:`

1. **Acción**:

- Al final del archivo `student_info.sh`, agrega esto:

```sh
echo -e "\nLast name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:"
```


### Paso 21 PSQL Consultas

Empieza por ver todos los datos de la tabla `courses`. Usa los comandos `SELECT` y `FROM` con `*`:

1. **Acción**:

- Ingresa `SELECT * FROM courses;`.

Puedes usar `LIKE` para encontrar patrones en el texto como este: `WHERE <column> LIKE '<pattern>'`. Un guion bajo `(_)` en un patrón devolverá filas que tengan cualquier carácter en esa posición. Visualiza las filas en esta tabla con un nombre de curso que coincida con el patrón `_lgorithms`:

2. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course LIKE '_lgorithms';`.

Otro carácter de patrón es `%`. Significa que puede haber cualquier cosa allí. Para encontrar nombres que comiencen con `W`, podrías usar `W%`. Visualiza los cursos que terminan en `lgorithms`:

3. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course LIKE '%lgorithms';`.

Intenta ver los cursos que comienzan con `Web`:

4. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course LIKE 'Web%';`.

Combina los dos caracteres de patrón para mostrar los cursos que tienen una segunda letra `e`:

5. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course LIKE '_e%';`.

 Intenta ver los cursos con un espacio en sus nombres. El patrón que quieres es `% %`:

 6. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course LIKE '% %';`.

Puedes usar `NOT LIKE` para encontrar cosas que no coincidan con un patrón. Visualiza los cursos que no contienen un espacio:

7. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course NOT LIKE '% %';`.

Intenta encontrar los que contienen una `A`. El patrón que quieres es `%A%`:

8. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course LIKE '%A%';`.

 `ILIKE` ignorará el caso de las letras al hacer coincidencias. Úsalo para ver los cursos con una 'A' o 'a': 

 9. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course ILIKE '%A%';`.

Puedes poner `NOT` delante de `ILIKE` también. Úsalo para ver los cursos que no contienen una 'A' o 'a':

10. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course NOT ILIKE '%A%';`.

Combina estos como cualquier otra condición. Aquí tienes un ejemplo: `SELECT * FROM courses WHERE course NOT ILIKE '<pattern>' AND course LIKE <pattern>;`: 

11. **Acción**:

- Ingresa `SELECT * FROM courses WHERE course NOT ILIKE '%A%' AND course LIKE '% %';`.


### Paso 22 Agregar echo

En tu script `student_info.sh`, añade una declaración `echo` al final, similar a las demás, para imprimir los resultados de la consulta sugerida.

1. **Acción**:

- Añade al final del archivo `student_info.sh`: 

```sh
echo "$($PSQL "SELECT last_name FROM students WHERE last_name ILIKE '%sa%' OR last_name LIKE '%r_'")"
```

2. **Acción**:

- Ejecuta el script `./student_info.sh` en la terminal de comandos.


### Paso 23 Agregar echo

Añade otra declaración `echo` al final, como las demás. Haz que esta diga: `"First name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:"`

1. **Acción**:

- Al final del archivo `student_info.sh`, añade esto:

```sh
echo -e "\nFirst name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:"
```


### Paso 24 PSQL Consultas

Comienza revisando todos los datos en la tabla de estudiantes:

1. **Acción**:

- Ingresa `SELECT * FROM students;`.

Todos los campos que están vacíos o en blanco son nulos. Puedes acceder a ellos usando IS NULL como condición así: WHERE <column> IS NULL. Visualiza a los estudiantes que no tienen GPA. La condición que necesitas es `gpa IS NULL`:

2. **Acción**:

- Ingresa `SELECT * FROM students WHERE gpa IS NULL;`

Puedes usar IS NOT NULL para ver filas que no son nulas. Visualiza toda la información de los estudiantes que tienen GPA: 

3. **Acción**:

- Ingresa `SELECT * FROM students WHERE gpa IS NOT NULL;`

Visualiza toda la información de los estudiantes que no han elegido una especialidad:

4. **Acción**:

- Ingresa `SELECT * FROM students WHERE major_id IS NULL;`

Visualiza a los estudiantes que no tienen una especialidad, pero no incluyas a los estudiantes sin GPA, la condición que necesitas es `major_id IS NULL AND gpa IS NOT NULL`:

5. **Acción**:

- Ingresa `SELECT * FROM students WHERE major_id IS NULL AND gpa IS NOT NULL;`

Visualiza a los estudiantes que no tienen una especialidad ni GPA, la condición que necesitas es `major_id IS NULL AND gpa IS NULL`:

6. **Acción**:

- Ingresa `SELECT * FROM students WHERE major_id IS NULL AND gpa IS NULL;`


### Paso 25 Agregar echo result

En el script, agrega un comando echo al final para imprimir los resultados que busca la oración. Añade `echo "$($PSQL "<query_here>")"`

1. **Acción**:

- Añade:

```sh
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE major_id IS NULL AND (first_name LIKE 'D%' OR gpa > 3.0)")"
```

2. **Acción**:

- Ejecutar el script `./student_info.sh`


### Paso 26 Agregar echo first five courses

Hay tres de ellos. Agrega otra oración, como las demás, que diga: `Course name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':`

1. **Acción**:

- Al final del archivo `student_info.sh`, añade esto:

```sh
echo -e "\nCourse name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':"
```


### Paso 27 PSQL Consultas

Puedes especificar el orden en el que deseas que se muestren tus resultados añadiendo `ORDER BY <column_name>` al final de una consulta. Aquí tienes un ejemplo: `SELECT <columns> FROM <table> ORDER BY <column>;`:

1. **Acción**:

- Ingresa `SELECT * FROM students ORDER BY gpa;`.

Eso puso los GPA más bajos en la parte superior. Al usar ORDER BY, se ordenará de forma ascendente (ASC) por defecto. Agrega DESC (descendente) al final de la última consulta para poner los más altos en la parte superior:

2. **Acción**:

- Ingresa `SELECT * FROM students ORDER BY gpa DESC;`.

Puedes agregar más columnas al orden separándolas con una coma así: `ORDER BY <column_1>, <column_2>`. Cualquier valor coincidente en la primera columna ordenada se ordenará por la siguiente:

3. **Acción**:

- Ingresa `SELECT * FROM students ORDER BY gpa DESC, first_name;`.

Puedes agregar `LIMIT <number>` al final de la consulta para obtener solo la cantidad que deseas:

4. **Acción**:

- Ingresa `SELECT * FROM students ORDER BY gpa DESC, first_name LIMIT 10;`.

El orden de las palabras clave en tu consulta importa. No puedes poner LIMIT antes de ORDER BY, ni ninguna de ellas antes de WHERE.  Visualiza el mismo número de estudiantes, en el mismo orden, pero no incluyas a los que no tienen un GPA:

5. **Acción**:

- Ingresa `SELECT * FROM students WHERE gpa IS NOT NULL ORDER BY gpa DESC, first_name LIMIT 10;`.


### Paso 28 Agregue echo result

En el script, añade el comando echo para imprimir las filas que la sentencia solicita.

1. **Acción**:

- Agregue:

```sh
echo "$($PSQL "SELECT course FROM courses WHERE course LIKE '_e%' OR course LIKE '%s' ORDER BY course DESC LIMIT 5")"
```

2. **Acción**:

- Ejecuta el script `./student_info.sh` en la terminal de comandos.


### Paso 29 Agregar echo

😎 Agrega otro comando echo al final del script como los demás. Haz que este diga: Promedio de GPA de todos los estudiantes redondeado a dos decimales

1. **Acción**:

- Agregue:

```sh
echo -e "\nAverage GPA of all students rounded to two decimal places:"
```


### Paso 30 PSQL Consultas

Existen varias funciones matemáticas que puedes usar con columnas numéricas. Una de ellas es MIN, que puedes usar al seleccionar una columna de esta manera: SELECT MIN(<columna>) FROM <tabla>. Encontrará el valor más bajo en la columna: 

1. **Acción**:

- Ingresa `SELECT MIN(gpa) FROM students;`.

Otra función es MAX, úsala para ver el GPA más alto de la misma tabla:

2. **Acción**:

- Ingresa `SELECT MAX(gpa) FROM students;`.

Usa la función SUM para averiguar qué suma todos los valores de la columna major_id en la tabla students:

3. **Acción**:

- Ingresa `SELECT SUM(major_id) FROM students;`.

AVG te dará el promedio de todos los valores en una columna:

4. **Acción**:

- Ingresa `SELECT AVG(major_id) FROM students;`.

Puedes redondear los decimales hacia arriba o hacia abajo al número entero más cercano con CEIL y FLOOR. Coloca AVG(major_id) dentro de los paréntesis de la función CEIL:

5. **Acción**:

- Ingresa `SELECT CEIL(AVG(major_id)) FROM students;`.

Puedes redondear un número al entero más cercano con ROUND:

6. **Acción**:

-  Ingresa `SELECT ROUND(AVG(major_id)) FROM students;`.

Puedes redondear a un número específico de decimales añadiendo una coma y el número a ROUND, así: ROUND(<número_a_redondear>, <lugares_decimales>):

7. **Acción**:

- Ingresa `SELECT ROUND(AVG(major_id), 5) FROM students;`.


### Paso 31 Agregar echo result

Agrega el comando para imprimirlo.

1. **Acción**:

- Agrega:

```sh
echo "$($PSQL "SELECT ROUND(AVG(gpa), 2) FROM students")"
```

2. **Acción**:

- Ejecutar el script `./student_info.sh` en la terminal de comandos.


### Paso 32 Agregar echo

Agregar el siguiente comando: `Major ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:`

1. **Acción**:

- agrega:

```sh
echo -e "\nMajor ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:"
```


### Paso 33 PSQL Consultas

Otra función es COUNT. Puedes usarla de la siguiente manera: `COUNT(<columna>)`. Esto te dirá cuántas entradas hay en una tabla para la columna:

1. **Acción**:

- Ingresa: `SELECT COUNT(*) FROM majors;`

Usando el mismo método, verifica cuántos estudiantes tienes:

2. **Acción**:

- Ingresa `SELECT COUNT(*) FROM students;`.

Visualiza el conteo de la columna major_id en la tabla de estudiantes para ver cuántos de tus estudiantes han elegido una especialidad:

3. **Acción**:

- Ingresa `SELECT COUNT(major_id) FROM students;`.

DISTINCT es una función que te mostrará solo los valores únicos. Puedes usarla de la siguiente manera: `DISTINCT(<columna>)`:

4. **Acción**:

- Ingresa `SELECT DISTINCT(major_id) FROM students;`.

 Puedes obtener los mismos resultados con GROUP BY. Aquí hay un ejemplo de cómo usarlo: `SELECT <columna> FROM <tabla> GROUP BY <columna>`:

 5. **Acción**:

- Ingresa `SELECT major_id FROM students GROUP BY major_id;`.

La salida fue la misma que DISTINCT, pero con GROUP BY puedes agregar cualquiera de las funciones de agregación (MIN, MAX, COUNT, etc.) para encontrar más información. Por ejemplo, si quisieras ver cuántos estudiantes hay en cada especialidad podrías usar `SELECT COUNT(*) FROM students GROUP BY major_id`:

6. **Acción**:

- Ingresa `SELECT major_id, COUNT(*) FROM students GROUP BY major_id;`.

Al usar GROUP BY, cualquier columna en el área SELECT debe estar incluida en el área GROUP BY. Otras columnas deben usarse con cualquiera de las funciones de agregación (MAX, AVG, COUNT, etc.). Visualiza los valores únicos de major_id con GROUP BY nuevamente, pero ve cuál es el GPA más bajo en cada uno de ellos:

7. **Acción**:

- Ingresa `SELECT major_id, MIN(gpa) FROM students GROUP BY major_id;`.

Introduce la misma consulta, pero agrega una columna que te muestre el GPA más alto en cada especialidad también:

8. **Acción**:

- Ingresa `SELECT major_id, MIN(gpa), MAX(gpa) FROM students GROUP BY major_id;`.

Otra opción con GROUP BY es HAVING. Puedes agregarlo al final de la consulta así: `SELECT <columna> FROM <tabla> GROUP BY <columna> HAVING <condición>`. La condición debe ser una función de agregación con una prueba. Un ejemplo podría ser usar `HAVING COUNT(*) > 0`:

9. **Acción**:

- Ingresa `SELECT major_id, MIN(gpa), MAX(gpa) FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;`.

Puedes renombrar una columna con AS así: `SELECT <columna> AS <nuevo_nombre_de_columna>`. Introduce el mismo comando, pero renombra la columna 'min a min_gpa':

10. **Acción**:

- Ingresa `SELECT major_id, MIN(gpa) AS min_gpa, MAX(gpa) FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;`.

Introduce el mismo comando, pero renombra también la columna max a max_gpa: 

11. **Acción**:

- Ingresa `SELECT major_id, MIN(gpa) AS min_gpa, MAX(gpa) AS max_gpa FROM students GROUP BY major_id HAVING MAX(gpa) = 4.0;`.

Visualiza major_id y el número de estudiantes en cada major_id en una columna llamada 'number_of_students':

12. **Acción**:

- Ingresa `SELECT major_id, COUNT(*) AS number_of_students FROM students GROUP BY major_id;`.

Usa HAVING con la última consulta para mostrar solo las filas con menos de ocho estudiantes en la especialidad:

13. **Acción**:

- Ingresa `SELECT major_id, COUNT(*) AS number_of_students FROM students GROUP BY major_id HAVING COUNT(*) < 8;`.


### Paso 34  Agrega echo para mostrar el resultado de la consulta

Agregar el comando `echo "$($PSQL "<consulta_aquí>")"` al final del archivo `student_info.sh` para imprimir los resultados sugeridos. 

1. **Acción**:

- Agrega

```sh
echo "$($PSQL "SELECT major_id, COUNT(*) AS number_of_students, ROUND(AVG(gpa),2) AS average_gpa FROM students GROUP BY major_id HAVING COUNT(*) > 1")"
```

2. **Acción**:

- Ejecutar el script `./student_info.sh` en la terminal de comandos.


### Paso 35 Agregar echo

Agrega un comando `echo` a tu script, como los otros, que imprima: `List of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':`


1. **Acción**:

- Al final del archivo `student_info.sh`, agrega esto:

```sh
echo -e "\nList of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':"
```


### Paso 36 Comandos JOIN

**psql students FULL JOIN majors:**

La unión FULL JOIN incluirá todas las filas de ambas tablas, tengan o no una fila que use esa clave foránea en la otra. A partir de ahí, podrías usar cualquiera de los métodos anteriores para filtrar, agrupar, ordenar, etc.


1. **Acción**:

- Si deseas ver el nombre de una especialidad que un estudiante está tomando, necesitas unir las dos tablas en una. Aquí tienes un ejemplo de cómo hacerlo: `SELECT * FROM <table_1> FULL JOIN <table_2> ON <table_1>.<foreign_key_column> = <table_2>.<foreign_key_column>;`

- Ingresa: `SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id;`


**psql students LEFT JOIN majors:**

Una LEFT JOIN obtiene todas las filas de la tabla izquierda, pero solo las filas de la tabla derecha que están vinculadas desde la izquierda. Une las tablas students y majors con una LEFT JOIN. Usa primero la tabla students cuando sea aplicable.

2. **Acción**:

- Escribe: `SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id;`


**psql students RIGHT JOIN majors:**

Una RIGHT JOIN devuelve todas las filas de la tabla de la derecha (la tabla después de JOIN), y las filas correspondientes de la tabla de la izquierda (la tabla antes de JOIN).

3. **Acción**:

- Une las mismas dos tablas con una RIGHT JOIN esta vez.

- Escribe: `SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id;`


**psql students INNER JOIN majors:**

Una INNER JOIN devuelve solo las filas donde hay coincidencia en ambas tablas. Es decir, solo se incluyen en el resultado las filas que tienen correspondencias en ambas tablas basadas en la condición de JOIN.

4. **Acción**:

- Une las tablas students y majors con una INNER JOIN. Usa primero la tabla students cuando sea aplicable.

- Escribe: `SELECT * FROM students INNER JOIN majors ON students.major_id = majors.major_id;`


### Paso 37 Ejercicios Prácticos de JOIN en SQL

Ahora deberías tener una idea sobre los cuatro tipos principales de JOIN. Intenta usar un `LEFT JOIN` para mostrar todas las especialidades, pero solo los estudiantes que tienen una especialidad:

1. **Acción**:
   
- Ingresa `SELECT * FROM majors LEFT JOIN students ON majors.major_id = students.major_id;`.


Ahora, usa el `JOIN` apropiado para mostrar solo los estudiantes que están inscritos en una especialidad, y solo las especialidades que tienen un estudiante inscrito. Quieres unir las tablas `students` y `majors` de nuevo.
Únelas con el `JOIN` que solo muestra filas si tienen un valor en la columna de clave foránea de la otra tabla.:

2. **Acción**:

-  Ingresa `SELECT * FROM majors INNER JOIN students ON majors.major_id = students.major_id;`.


Intenta usar un RIGHT JOIN para mostrar todos los estudiantes, pero solo las especialidades si un estudiante está inscrito en ellas. Une las tablas `students` y `majors` de nuevo:

3. **Acción**:

- Ingresa `SELECT * FROM majors RIGHT JOIN students ON majors.major_id = students.major_id;`.


Usa el `JOIN` apropiado con las mismas dos tablas para mostrar todas las filas en ambas tablas, independientemente de si tienen un valor en la columna de clave foránea o no:

4. **Acción**:

- Ingresa `SELECT * FROM majors FULL JOIN students ON majors.major_id = students.major_id;`.


### Paso 38 PSQL Consultas

**psql SELECT * students INNER JOIN majors**

Usa el `JOIN` que muestre solo a los estudiantes que tienen una especialidad (majors) y solo a las especialidades que tienen un estudiante, sin agregar ninguna condición:

1. **Acción**:

- Escribe: `SELECT * FROM students INNER JOIN majors ON students.major_id = majors.major_id;`.

**psql SELECT major students INNER JOIN majors**

Escribe el mismo comando, pero solo selecciona la columna que necesitas. Solo necesitas la columna `major`:

2. **Acción**:

- Escribe `SELECT major FROM students INNER JOIN majors ON students.major_id = majors.major_id;`.

**psql SELECT DISTINCT(major) students INNER JOIN majors**

Usa `DISTINCT` para devolver solo los valores únicos y ver la lista de especialidades que tienen estudiantes. Debes cambiar `major` de la consulta anterior a `DISTINCT(major)`:

3. **Acción**:

- Escribe `SELECT DISTINCT(major) FROM students INNER JOIN majors ON students.major_id = majors.major_id;`.

**psql SELECT * students RIGHT JOIN majors**

Supongamos que quieres una lista de las especialidades que los estudiantes no están cursando. Usa el JOIN más eficiente para unir las dos tablas que necesitas. Solo une las tablas por ahora, no utilices ninguna otra condición:

4. **Acción**:

- Escribe `SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id; en el prompt de psql.`.

**psql SELECT * students RIGHT JOIN majors WHERE student_id IS NULL**

Ahora puedes ver las que no tienen estudiantes. Agrega una condición WHERE para ver solo las especialidades sin estudiantes, utilizando `student_id` en la condición:

5. **Acción**:

- Escribe `SELECT * FROM students RIGHT JOIN majors ON students.major_id = majors.major_id WHERE student_id IS NULL;`.

**psql SELECT major students RIGHT JOIN majors WHERE student_id IS NULL**

Selecciona solo las columnas necesarias para ver la lista de especialidades sin estudiantes. La columna que necesitas es `major`:

6. **Acción**:

- Escribe `SELECT major FROM students RIGHT JOIN majors ON students.major_id = majors.major_id WHERE student_id IS NULL;`.

**psql SELECT * students LEFT JOIN majors**

Usa el JOIN más eficiente para unir las tablas necesarias si se te pidiera obtener el nombre, apellido, especialidad y GPA de los estudiantes que están cursando Data Science o tienen un GPA de 3.8 o más. Solo une las tablas por ahora, no utilices ninguna otra condición:

7. **Acción**:

- Escribe `SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id;`.

**psql SELECT students LEFT JOIN majors WHERE major = Data Science OR gpa >= 3.8**

Usa WHERE para obtener solo los estudiantes que cumplen con los requisitos. Como recordatorio, el objetivo era encontrar estudiantes que estén cursando Data Science o que tengan un GPA de 3.8 o más. Debes agregar dos condiciones para verificar la columna `major` y otra para la columna `gpa`:

8. **Acción**:

- Escribe `SELECT * FROM students LEFT JOIN majors ON students.major_id = majors.major_id WHERE major='Data Science' OR gpa >= 3.8;`.

**psql SELECT columns LEFT JOIN WHERE major = Data Science OR gpa >= 3.8**

Escribe el mismo comando, pero selecciona solo las columnas que necesitas. Habían cuatro: el nombre del estudiante, apellido, su especialidad y GPA. Selecciónalos en ese orden: 

9. **Acción**:

- Escribe `SELECT first_name, last_name, major, gpa FROM students LEFT JOIN majors ON students.major_id = majors.major_id WHERE major='Data Science' OR gpa >= 3.8;`.

**psql SELECT * students FULL JOIN majors**

Usa el JOIN más eficiente para unir todas las tablas necesarias si quisieras obtener la lista de estudiantes y sus cursos, con un enfoque particular en los estudiantes que no tienen ningún curso asignado todavía y cursos que no tienen ningún estudiante inscrito. Solo une las tablas por ahora, no utilices ninguna otra condición:

10. **Acción**:

- Escribe `SELECT * FROM students FULL JOIN courses ON students.course_id = courses.course_id;`.

**psql SELECT * students FULL JOIN majors WHERE first_name || major LIKE ri**

Agrega una cláusula `WHERE` a la consulta anterior para obtener solo las filas que necesitas. Las filas que querías eran aquellas con un nombre o especialidad que contuvieran "ri":

11. **Acción**:

- Escribe `SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE first_name LIKE '%ri%' OR major LIKE '%ri%';`.

**psql SELECT major FROM students FULL JOIN majors WHERE first_name || major LIKE ri**

Solo querías mostrar las columnas `first_name` y `major`. Ingresa la consulta anterior, pero solo obtén las columnas que necesitas:

12. **Acción**:

- Escribe `SELECT first_name, major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE first_name LIKE '%ri%' OR major LIKE '%ri%';`.


### Paso 39 Agrega echo

Agrega el comando para imprimir lo que la instrucción está pidiendo.

1. **Acción**:

- Agrega:

```sh
echo "$($PSQL "SELECT major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE major IS NOT NULL AND (student_id IS NULL OR first_name ILIKE '%ma%') ORDER BY major")"
```

2. **Acción**:

- Ejecuta el script `./student_info.sh` en la terminal.


### Paso 40  Agregar echo para cursos sin estudiantes o 'Obie Hilpert'

En el script, agrega un comando para imprimir esta frase como las demás: Lista de cursos únicos, en orden alfabético inverso, que ningún estudiante o 'Obie Hilpert' está tomando:

1. **Acción**:

- Al final del archivo `student_info.sh`, agrega:

```sh
echo -e "\nList of unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking:"
```


### Paso 41 PSQL Consultas

**psql SELECT * FROM students FULL JOIN majors**

Comienza haciendo un FULL JOIN en tus tablas de `students` y `majors`:

1. **Acción**:

- Escribe `SELECT * FROM students FULL JOIN majors ON students.major_id = majors.major_id;`.

**psql SELECT students.major_id students FULL JOIN majors**

Si observas los nombres de las columnas, verás dos columnas `major_id`: una de la tabla `students` y otra de la tabla `majors`. Si intentas consultarlas usando solo `major_id`, obtendrás un error. Necesitarás especificar de qué tabla quieres la columna, así: `<table>.<column>`. Ingresa el mismo JOIN pero obteniendo solo la columna `major_id` de la tabla `students`:

2. **Acción**:

- Escribe `SELECT students.major_id FROM students FULL JOIN majors ON students.major_id = majors.major_id;`.

**psql SELECT students.major_id FROM students FULL JOIN majors AS m**

Utilizaste 'AS' para renombrar columnas. También puedes usarlo para renombrar tablas o darles alias. Aquí tienes un ejemplo: `SELECT * FROM <table> AS <new_name>;`. Ingresa la misma consulta que acabas de hacer, pero renombra la tabla `majors` como 'm':

3. **Acción**:

- Escribe `SELECT students.major_id FROM students FULL JOIN majors AS m ON students.major_id = m.major_id;`.

**psql SELECT s.major_id FROM students AS s FULL JOIN majors AS m**

 Ingresa la misma consulta, pero renombra la tabla `students` como 's' también:

 4. **Acción**:

- Escribe `SELECT s.major_id FROM students AS s FULL JOIN majors AS m ON s.major_id = m.major_id;`.

**psql SELECT * FROM students FULL JOIN majors USING**

Hay una palabra clave de acceso directo, `USING`, para hacer JOIN entre tablas si la columna de clave foránea tiene el mismo nombre en ambas tablas. Aquí tienes un ejemplo: `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>);`:

5. **Acción**:

- Escribe `SELECT * FROM students FULL JOIN majors USING(major_id);`.

**psql SELECT * FROM students FULL JOIN majors USING FULL JOIN major_courses USING**

Puedes agregar una tercera tabla a un JOIN así: `SELECT * FROM <table_1> FULL JOIN <table_2> USING(<column>) FULL JOIN <table_3> USING(<column>)`. Este ejemplo unirá las dos primeras tablas en una, convirtiéndola en la tabla izquierda para el segundo JOIN. Usa este método para unir las dos tablas de la consulta anterior con la tabla `majors_courses`:

6. **Acción**:

- Escribe `SELECT * FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id);`.

**psql SELECT * students FULL JOIN majors USING JOIN major_courses USING JOIN courses USING**

Puedes unir tantas tablas como quieras. Une la última tabla a la consulta anterior para obtener los nombres de los cursos con toda esta información:

7. **Acción**:

- Escribe `SELECT * FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id) FULL JOIN courses USING(course_id);`.


### Paso 42 Agregar echo result

En el script, agrega el comando para imprimir la información sugerida. 

1. **Acción**:

- Agrega

```sh
echo "$($PSQL "SELECT DISTINCT(course) FROM students RIGHT JOIN majors USING(major_id) INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) WHERE (first_name = 'Obie' AND last_name = 'Hilpert') OR student_id IS NULL ORDER BY course DESC")"
```

2. **Acción**:

- Ejecuta el script `./student_info.sh` e la terminal.


### Paso 43 Agregar echo para cursos con solo un estudiante

Último paso. Añade un comando que imprima la frase: `List of courses, in alphabetical order, with only one student enrolled:`:

1. **Acción**:

- Agrega al  final del archivo `student_info.sh`:

```sh
echo -e "\nList of courses, in alphabetical order, with only one student enrolled:"
```


### Paso 44 Agregar resultado de consulta con echo

Añade un comando al final del script para imprimir la información sugerida:

1. **Acción**:

- Agrega al  final del archivo `student_info.sh`:

```sh
echo "$($PSQL "SELECT course FROM students INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) GROUP BY course HAVING COUNT(student_id) = 1 ORDER BY course")"
```

2. **Acción**:
   
- Ejecuta el script una última vez. 👋.



### Archivo  `student_info.sh`

```sh
#!/bin/bash

# Info about my computer science students from students database

echo -e "\n~~ My Computer Science Students ~~\n"

PSQL="psql -X --username=freecodecamp --dbname=students --no-align --tuples-only -c"

echo -e "\nFirst name, last name, and GPA of students with a 4.0 GPA:"
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE gpa = 4.0")"

echo -e "\nAll course names whose first letter is before 'D' in the alphabet:"
echo "$($PSQL "SELECT course FROM courses WHERE course < 'D'")"

echo -e "\nFirst name, last name, and GPA of students whose last name begins with an 'R' or after and have a GPA greater than 3.8 or less than 2.0:"
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE last_name >= 'R' AND (gpa > 3.8 OR gpa < 2.0)")"

echo -e "\nLast name of students whose last name contains a case insensitive 'sa' or have an 'r' as the second to last letter:"
echo "$($PSQL "SELECT last_name FROM students WHERE last_name ILIKE '%sa%' OR last_name ILIKE '%r_'")"

echo -e "\nFirst name, last name, and GPA of students who have not selected a major and either their first name begins with 'D' or they have a GPA greater than 3.0:"
echo "$($PSQL "SELECT first_name, last_name, gpa FROM students WHERE major_id IS NULL AND (first_name LIKE 'D%' OR gpa > 3.0)")"

echo -e "\nCourse name of the first five courses, in reverse alphabetical order, that have an 'e' as the second letter or end with an 's':"
echo "$($PSQL "SELECT course FROM courses WHERE course LIKE '_e%' OR course LIKE '%s' ORDER BY course DESC LIMIT 5")"

echo -e "\nAverage GPA of all students rounded to two decimal places:"
echo "$($PSQL "SELECT ROUND(AVG(gpa), 2) FROM students")"

echo -e "\nMajor ID, total number of students in a column named 'number_of_students', and average GPA rounded to two decimal places in a column name 'average_gpa', for each major ID in the students table having a student count greater than 1:"
echo "$($PSQL "SELECT major_id, COUNT(*) AS number_of_students, ROUND(AVG(gpa), 2) AS average_gpa FROM students GROUP BY major_id HAVING COUNT(*) > 1")"

echo -e "\nList of majors, in alphabetical order, that either no student is taking or has a student whose first name contains a case insensitive 'ma':"
echo "$($PSQL "SELECT major FROM students FULL JOIN majors ON students.major_id = majors.major_id WHERE major IS NOT NULL AND (student_id IS NULL OR first_name ILIKE '%ma%') ORDER BY major")"

echo -e "\nList of unique courses, in reverse alphabetical order, that no student or 'Obie Hilpert' is taking:"
echo "$($PSQL "SELECT DISTINCT(course) FROM students FULL JOIN majors USING(major_id) FULL JOIN majors_courses USING(major_id) FULL JOIN courses USING(course_id) WHERE student_id IS NULL OR (first_name = 'Obie' AND last_name = 'Hilpert') ORDER BY course DESC")"

echo -e "\nList of courses, in alphabetical order, with only one student enrolled:"
echo "$($PSQL "SELECT course FROM students INNER JOIN majors_courses USING(major_id) INNER JOIN courses USING(course_id) GROUP BY course HAVING COUNT(student_id) = 1 ORDER BY course")"

```
