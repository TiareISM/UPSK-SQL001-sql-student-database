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


### Paso 12 psql SQL Consultas

SQL significa "Structured Query Language" (Lenguaje de Consulta Estructurado). Es el lenguaje que has estado usando para gestionar tus bases de datos relacionales. 
En el prompt de `psql`, visualiza todos los datos en la tabla students como lo has hecho muchas veces.

1. **Acción**:

- Ingresa `SELECT * FROM students;` en el prompt de psql.

Para ver solo una columna específica de una tabla.

2. **Acción**:

- Ingresa `SELECT first_name FROM students;` en el prompt de psql.

Para devolver múltiples columnas, sepáralas con comas en tu consulta.

3. **Acción**:

- Ingresa `SELECT first_name, last_name, gpa FROM students;` en el prompt de psql.

Para devolver solo las filas que cumplan con una condición específica, agrega ` WHERE <condición>` a tu consulta.

4. **Acción**:

- Usa `WHERE gpa < 2.5`.

Para mostrar filas donde el `gpa` sea mayor o igual a un valor específico, usa el operador `>=`. 

5. **Acción**:

- Usa `WHERE gpa >= 3.8`.

Para devolver filas donde el `gpa` no sea igual a un valor específico, usa el operador `!=`.

6. **Acción**:

- Ingresa `SELECT first_name, last_name, gpa FROM students WHERE gpa != 4.0;` en el prompt de psql.

### Paso 13 

