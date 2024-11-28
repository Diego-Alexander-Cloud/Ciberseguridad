## Algoritmo Para Actualizaciones De Archivos De Seguridad En Python
<br>

### Descripción:

Como parte de las responsabilidades dentro de la empresa, se me informa que debo actualizar periódicamente un archivo que identifica al personal con acceso a contenido restringido. Me indican que al personal se le restringe en acceso según su dirección IP y que existe una lista de direcciones IP autorizadas para acceder a la subred restringida. También se cuenta con una lista de eliminación que identifica qué empleados debo remover de la lista de autorizaciones.

El archivo que identifica las direcciones IP permitidas se denomina “allow_list.txt”, mientras que el archivo que identifica las direcciones IP que ya no deberían tener acceso se nombra ”remove_list.txt”. Por tanto, para desarrollar esta tarea hice un algoritmo para automatizar la actualización del archivo allow_list.txt, y eliminar estas direcciones IP que han perdido el derecho de acceder a la subred restringida, el cual muestro a continuación.
<br>

### Abrir El Archivo Con La Lista De Permisos
<br>

Lo primero que hice para abrir el archivo “allow_list.txt” en este algoritmo, fue asignarle el nombre de “import_file”:

![Imagen_1](https://github.com/user-attachments/assets/5b3d0764-aa48-4f3d-ad5e-0a5abf7ad4a5)
Imagen 1

Ahora para abrir el archivo uso la sentencia ”with”:

![Imagen_2](https://github.com/user-attachments/assets/d67324dc-c7d4-4cc0-8981-73fa37cf7fcd)
Imagen 2

Aquí usé la sentencia “with” junto con la función ”.open()” en modo lectura para poder abrir y leer el archivo de la lista de usuarios permitidos, con esto puedo acceder a las direcciones IP almacenadas. La función “open” en esta línea “with open(import_file, “r”) as file:” tiene dos parámetros, el primero identifica el archivo que estoy importando, y el segundo, en este caso “r” indica que quiero leerlo. Adicionalmente también usé la palabra clave “as” para asignarle la variable llamada “file”, que almacenará la salida de la función “.open()”.
<br>

### Leer El Contenido Del Archivo
<br>

Para leer el archivo uso el método “.read()” y al tiempo lo convierto en cadena.

![Imagen_3](https://github.com/user-attachments/assets/a37506ee-5b6a-476c-bad9-b57096c862b3)
Imagen 3

Cuando uso la función “.open()” con el argumento “r” para leer el archivo, puedo usar la función “.read()” en el cuerpo de la sentencia “with”. El método “.read()” me permite convertir el archivo en una cadena y también leerlo, por tanto apliqué el método “.read()” a la variable “file” identificada en la sentencia “with” y luego asigné la cadena de salida a la variable “ip_addresses”.
Como aclaración, este código lee el contenido del archivo “allow_list.txt” en un formato de cadena que permitirá mas adelante organizar y extraer los datos que quiera.
<br>

### Convertir La Cadena En Una Lista
<br>

Como requiero eliminar direcciones IP de la lista de permisos, necesitaba que el archivo estuviera en formato lista, ahora usando el método “.split()” puedo convertir la cadena “ip_addresses” en una lista:

![Imagen_4](https://github.com/user-attachments/assets/6212d4ee-8300-4dec-92eb-a38f47cf7d35)
Imagen 4

Lo que hace la función “.split()” es convertir el contenido de una cadena en una lista. La idea es dividir “ip_addresses” en una lista para facilitar la eliminación de direcciones IP de la lista de direcciones permitidas. De forma predeterminada la función “.split()” separa el texto por espacios en blanco en elementos de una lista.
Resumiendo, la función “.split()” toma los datos almacenado en la variable “ip_addresses” (que es una cadena de direcciones IP que están separadas por un espacio en blanco) y convierte esta cadena en una lista de direcciones IP. Para almacenar esta lista, la reasigné a la variable “ip_addresses”.
<br>

### Iterar A Través De La Lista De Eliminación
<br>

Ahora necesito iterar las direcciones IP de “remove_list” para en un futuro poder eliminar una a una las direcciones IP que ya no tendrán acceso a la subred restringida, para esto utilizo un bucle “for”:

![Imagen_5](https://github.com/user-attachments/assets/5231febb-1545-4d06-82b5-274e39010ec8)
Imagen 5

Lo que quiero que haga el bucle “for” es aplicar una secuencia específica a todos los elementos de lista. La palabra “for” inicia el bucle “for”, seguido por la variable del bucle “element”, la palabra clave “in” que indica iterar a través de la lista “ip_addresses” y asigna cada valor de esta a la variable del bucle “element”.
<br>

### Eliminar Direcciones IP Que Están En La Lista De Eliminación
<br>

Continuado con el bucle “for” ahora me dispongo a borrar las direcciones IP de la lista de permitidos “ip_addresses”, que se encuentran en “remove_list”. Dado que todos los elementos de “remove_list” están dentro de la lista “ip_addresses” y que esta lista tampoco contiene duplicados, puedo usar el método “.remove()” en mi bucle “for” así:

![Imagen_6](https://github.com/user-attachments/assets/4659a312-4de7-4489-8f58-a16ee8cc36df)
Imagen 6

Apliqué el método “.remove()” para eliminar de la lista “ip_addresses” los elementos que se encuentran en “remove_list”, dando como variable del bucle “element” para que cada dirección IP que estaba en “remove_list” se eliminara de “ip_addresses”, es decir que al finalizar el bucle, todas las direcciones IP que no deberían tener acceso a la subred ya no se encontrarán dentro de la lista “ip_addresses”.
<br>

### Actualizar El Archivo Con La Lista Revisada De Direcciones IP
<br>

Por último necesito actualizar el archivo de la lista permitidos con la nueva actualización de las direcciones IP, para esto, primero tuve que convertir la lista de nuevo en una cadena usando el método “.join()”:

![Imagen_7](https://github.com/user-attachments/assets/70d8db76-768c-42f1-870b-0672c2024763)
Imagen 7

Con el método “.join()” combino todos los elementos resultantes de iteración en una cadena. Es decir, utilicé el “.join()” para crear una cadena a partir de la lista “ip_addresses” para poder pasarla como argumento en un siguiente paso al archivo “allow_list.txt”. Para complementar, el espacio(“ “) en el código lo usé como separador.

Luego utilicé la sentencia “with” con el método “.write()” para actualizar el archivo:

![Imagen_8](https://github.com/user-attachments/assets/50011140-b02f-451c-829f-cdc90ba87fc2)
Imagen 8

Esta vez en mi sentencia “with” utilizo dentro del “open()” el argumento “w” que indica que quiero escribir dentro del archivo. En el paso anterior hice la cadena”ip_addresses” para poder pasarla como argumento, en este caso a la fusión “.write()” para poder escribir los datos resultantes en un archivo específico y reemplazar el contenido del archivo, que en este caso es “ip_addresses”.

**En conclusión**, establecí un algoritmo que toma el archivo “allow_list.txt” que es el archivo en donde se encuentran las direcciones IP con permiso de acceso a la subred restringida y, eliminé de este las direcciones IP que se encuentran en la lista “remove_list.txt”, que identifica a las direcciones IP que ya no deben tener acceso a la subred. Para esto convertí el archivo “allow_list.txt” en una cadena para leerlo, después volverlo en una lista almacenada en la variable “ip_addresses” e iteré a través de las direcciones IP de “remove_list” para poder eliminar las direcciones IP de las lista “ip_addresses” con el método “.remove()”, entonces usé el método “.join()” para volver a convertir “ip_addresses” en una cadena y después en una lista, para finalmente sobrescribir el archivo “allow_list.txt” y dejarlo actualizado.

