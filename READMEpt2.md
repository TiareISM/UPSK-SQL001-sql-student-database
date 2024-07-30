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


### Paso 22 
