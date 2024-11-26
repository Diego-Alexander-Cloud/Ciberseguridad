## Aplicar Filtros A Consultas SQL Para Realizar Tareas De Seguridad
<br>
  
### Descripción 
<br>
  
Mi empresa está trabajando para que el sistema sea más seguro, por tanto, deberé garantizar que el sistema esté protegido, y por eso voy a investigar los posibles problemas de seguridad y actualizar los computadores según sea necesario. Los siguientes ejemplos muestran la forma en que usé SQL con filtros para realizar tareas de seguridad.
<br>

### Recuperar Intentos De Inicio De Sesión Fallidos Después Del Horario Laboral
<br>

Se produjo un posible incidente de seguridad después del horario laboral (6:00 p.m.). Fue necesario investigar todos los intentos de inicio de sesión fallidos después del horario laboral.

En el siguiente código muestro cómo hice una consulta SQL para filtrar los intentos de inicio de sesión fallidos que tuvieron lugar después del horario laboral.

![imagen_1](https://github.com/user-attachments/assets/b0629a61-ebbb-4dbd-b217-29811f3a5163)
Imagen 1

La primera parte de la captura de pantalla es mi consulta, y la segunda es un fragmento del resultado. Esta consulta filtra los inicios de sesión fallidos después de las 6:00 p.m. que es cuando termina la jornada laboral. Lo primero que hice fue seleccionar todos los datos de la tabla log_in_attempts (intentos de sesión), después usé la cláusula `WHERE` con el operador `AND` para filtrar los resultados y, de esta manera obtener solo los intentos de sesión fallidos, a continuación utilicé la condición `login_time > ’18:00’` que filtra los intentos de sesión hechos después de las 18:00 o 6:00 p.m. La condición `success = FALSE`, filtra por intentos de sesión fallidos.
<br>

### Recuperar Intentos De Inicio De Sesión En Fechas Específicas
<br>

Se reportó un evento sospechoso el 09-05-2022 y se requiere investigar toda la actividad registrada el 09-05-2022 o el día anterior.

El código siguiente demuestra cómo creé la consulta SQL para filtrar por intentos de inicio de sesión en fechas específicas.

![imagen_2](https://github.com/user-attachments/assets/e678c6dd-f1c3-45d2-b622-08b7b2c67ad0)
Imagen 2

Las tres primeras líneas de la captura de pantalla corresponden a mi consulta, el resto es una fracción del resultado. Esta consulta muestra todos los intentos de sesión comprendidos entre el 09-05-2022 o el 08-05-2022. Comencé seleccionado la tabla log_in_attempts (intentos de inicio de sesión), a continuación, usé la cláusula `WHERE` con el operador `OR` para filtrar los resultados comprendidos entre el 09-05-2022 o el 08-05-2022 y, agregué las condiciones `login_date = ‘2022-05-09’` y `login_date = ‘2022-05-08’` para filtrar los inicios de sesión ocurridos en ese trascurso de tiempo.
<br>

### Recuperar Intentos De Inicio De Sesión Fuera De México
<br>

Tras haber investigado los resultados de intentos de inicio de sesión en la organización, sospecho que existe un problema con los intentos de inicio de sesión realizados fuera de Méjico, por tanto estos deben ser investigados.

El código a continuación, presenta la forma en que realicé la consulta SQL para filtrar los intentos de inicio de sesión ocurridos fuera de Méjico.

![imagen_3](https://github.com/user-attachments/assets/eabed9cb-c2aa-4b01-95fa-10b267f34c78)
Imagen 3

La primera parte de la captura de pantalla es mi consulta, y la segunda es un fragmento del resultado. La consulta devuelve todos los intentos de inicio de sesión que ocurrieron fuera de Méjico. Lo primero fue seleccionar los datos de la tabla log_in_attempts (intentos de inicio de sesión), posteriormente usé la cláusula `WHERE` con `NOT` para filtrar por los países que no son Méjico. Usé `LIKE` con `MEX%` como el patrón de coincidencia, porque la base de datos representa a Méjico como MEX y MEXICO. El signo de porcentaje (%) representa cualquier número de caracteres cuando se usa junto con `LIKE`.
<br>

### Consulta De Equipos Para Actualizar En Marketing
<br>

La empresa requiere actualizar los computadores de algunos empleados del departamento de Marketing en el edificio Este (East), para hacerlo necesito saber cuáles son los equipos de los empleados que debo actualizar.

A continuación muestro el código que escribí para realizar la consulta SQL que filtra por equipo de empleado en el departamento de Marketing en el edificio Este (East).

![imagen_4](https://github.com/user-attachments/assets/d10e0dc0-a014-4c70-949d-d91da56dfb63)
Imagen 4

Las primeras líneas de la captura de pantalla corresponden a mi consulta, y el resto corresponden a una parte de la respuesta. Esta consulta enseña todos los empleados del departamento de Marketing del edificio Este. Para realizar la consulta, seleccioné todos los datos de la tabla employees (empleados), seguí con una cláusula `WHERE` junto con `AND` para filtrar los empleados que trabajan en el departamento de Marketing en el edificio Este (East). Apliqué `LIKE` con `East%` para el patrón de coincidencia de los datos de la columna office (oficina) con el edificio East (Este). La primera condición `department = ‘Marketing’` filtra los empleados del departamento de Marketing, y la segunda, `office LIKE ‘East%’` filtra los empleados que se encuentra en el edificio Este (East).
<br>

### Consulta De Empleados En Finanzas Y Ventas
<br>

También se requiere actualizar los equipos de los empleados de los departamentos de Finanzas y Ventas, como la actualización de estos equipos es diferente, solo me interesa la información de los empleados que trabajan dentro de esos departamentos.

En el código siguiento expongo la forma en que realicé la consulta SQL para obtener el registro de empleado de los departamentos de Finanzas (Finance) y Ventas (Sales).

![imagen_5](https://github.com/user-attachments/assets/92115673-e786-46d3-b6f8-dee5d24938ae)
Imagen 5

En las tres primeras líneas de la captura de pantalla aparece mi consulta, en el resto aparece una porción del resultado. En esta consulta se muestran todos los empleados que trabajan en los departamentos de Finanzas (Finance) y Ventas (Sales). Primero seleccioné todos los trabajadores de la tabla employees (empleados), continué con el uso de la cláusula `WHERE` junto con `OR` para filtrar a los empleados de Finanzas y Ventas. Usé `OR` en vez de `AND`, porque quería tener la lista de todos los empleados de los dos departamentos. La primera condición `department = ‘Finance’` filtra a los empleados de Finanzas y la segunda `department = ‘Sales’` filtra a los empleados de Ventas.
<br>

### Consulta De Todos Los Empleados Que No Trabajan En TI
<br>

La empresa requiere que se haga una actualización de los equipos de los empleados que no trabajan en el departamento de Tecnología de la Información, para hacer esto debo tener la información de todos esos empleados.

En el siguiente código muestro cómo realicé la consulta SQL para obtener los equipos por empleado que no trabajan en el departamento de Tecnología de la Información.

![imagen_6](https://github.com/user-attachments/assets/79ca7ecb-07e7-4602-b9cc-39bd588cfa38)
Imagen 6

Las tres primeras líneas de la captura de pantalla corresponden a mi consulta, el resto es una fracción del resultado. En esta consulta se muestran todos los empleados que no trabajan en el departamento de TI. Lo primero que hice fue seleccionar la tabla employees (empleados) y, usando la cláusula `WHERE` con `NOT` filtré los empleados que no trabajaban en el departamento de Tecnología de la Información.
<br>

**En conclusión**, apliqué filtros para consultas SQL para obtener información específica sobre los intentos de inicio de sesión fallidos y de los equipos de los empleados de la empresa. Utilicé una base de datos que contiene dos tablas distintas, log_in_attempts (intentos de inicio de sesión) y employees (empleados). Utilicé los operadores AND, OR, NOT y LIKE, como también el comodín de signo de porcentaje (%) para filtrar patrones y obtener la información específica que necesitaba para cada tarea.


