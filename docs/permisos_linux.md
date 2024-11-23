### Cambiando Permisos De Archivos En Linux
<br>

**Descripción:**

El equipo de la empresa necesita actualizar los permisos de los archivos para algunos archivos y directorios del directorio “projects”. En estos momentos los permisos y autorizaciones deben revisarse y actualizarse ya que no presentan las autorizaciones que deben otorgarse.

**Pasos:**

1. Revisar los detalles de los archivos y el directorio
2. Examinando la cadena de permisos
3. Cambiando permisos de archivo
4. Cambiando los permisos de un archivo oculto
5. Cambiando permisos de directorio
<br>
<br>

**1. Revisar los detalles de los archivos y el directorio**
<br>
<br>

La siguiente imagen muestra los comandos que utilicé para determinar los permisos establecidos para el directorio específico en el sistema de archivos:

![imagen_1](https://github.com/user-attachments/assets/9eb91ec3-fd4e-45ae-a204-147668254249)
Imagen 1

En esta imagen se ve la lista detallada con los archivos ocultos del contenido del directorio “projects”, para esto usé el comando ls con la opción -la, la salida del comando muestra que hay un directorio llamado “drafts”, un archivo oculto “.project_x.txt” y cinco archivos de proyecto. La cadena de 10 caracteres de la primera columna muestra los permisos establecidos para cada archivo y directorio.
<br>
<br>

**2. Examinando la cadena de permisos**
<br>
<br>

La cadena de 10 caracteres (cadena de permisos) se puede desglosar para determinar quién tiene autorización para acceder a los archivos y los permisos que posee. Los caracteres y lo que significa lo explico a continuación:

Ejemplo de cadena:   **drwxr-xrw-** 
La desgloso así:	   d  rwx  r-x    r w -
Número de carácter:  1  234  567    8 9 10

**El carácter 1** es una d cuando es un directorio, si fuera un archivo se indicaría con un guion (-).

**Los caracteres 2, 3 y 4** corresponden a los permisos de lectura (r), escritura (w) y ejecución (x) para el usuario. Cuando uno de estos caracteres es un guion (-) en vez de una letra, indica que no se le ha concedido este permiso al usuario, en este ejemplo el usuario tiene todos los permisos.

**Los caracteres 5, 6 y 7** indican los permisos de lectura (r), escritura (w) y ejecución (x) del grupo, en este caso el carácter 6 es un guion (-), lo que significa que el grupo no tiene permisos de escritura.

**Los caracteres 8, 9 y 10** muestran los permisos de lectura (r), escritura (w) y ejecución (x) para otros usuarios. Este tipo de propietario hace referencia a todos los demás usuarios del sistema aparte del usuario y del grupo. En este ejemplo el carácter 10 es un guion (-), lo que indica que los otros usuarios no tienen permiso de ejecución.

Teniendo en cuenta esta información voy a cambiar los permisos de archivo que correspondan.
<br>
<br>

**3. Cambiando permisos de archivo**
<br>
<br>

La empresa determinó que solo los usuarios involucrados con los proyectos deben tener permiso de escritura, los otros usuarios no deberían tener este privilegio de escritura. Teniendo en cuenta esto, puedo ver en la imagen 1 que el archivo project_k.txt tiene permiso de escritura para otros usuarios. En la siguiente imagen (Imagen 2) muestro cómo usé los comandos Linux para eliminar los privilegios de escritura del archivo project_k.txt para otros usuarios:

![imagen_2](https://github.com/user-attachments/assets/296b1814-f215-4752-a6fd-51a257756db9)
Imagen 2

Las dos primeras líneas muestran los comandos que ingresé, las siguientes muestran la salida del comando `ls`. Usé el comando `chmod` para cambiar los permisos de escritura del archivo y luego usé el comando `ls -la` para revisar que este correcto.
<br>
<br>

**4. Cambiando los permisos de un archivo oculto**
<br>
<br>

La empresa decidió archivar project_x.txt, no quieren que nadie tenga acceso de escritura a este proyecto, pero el usuario y el grupo deben tener acceso de lectura. A continuación, muestro el código que usé para cambiar los permisos:

![imagen_3](https://github.com/user-attachments/assets/adc43a53-d6e0-4c5d-b6fe-8dbc2e72bb63)
Imagen 3

La primera y segunda línea muestran los comandos que ingresé y las otras líneas la salida del segundo comando. El archivo .project_x.txt es un archivo oculto, lo sé porque comienza con punto (.). En este ejemplo, eliminé los permisos de escritura del usuario (con u-w) y del grupo (con g-w), después agregué permisos de lectura para el grupo (con g+r). 
<br>
<br>

**5. Cambiando permisos de directorio**
<br>
<br>

La empresa solo quiere que el usuario fénix tenga acceso al directorio drafts y sus contenidos; esto significa que nadie más que fénix debe tener permisos de ejecución. En la siguiente imagen muestro cómo utilicé los comandos de Linux para cambiar los permisos:

![imagen_4](https://github.com/user-attachments/assets/d06749cc-ccef-4835-b344-520e22dfec89)
Imagen 4

Como ya se evidencia las dos primeras líneas muestran los comandos que ingresé y las otras muestran la salida del segundo comando. En la imagen 1 ya se había determinado que el grupo tenía permiso de ejecución, así que usé el comando `chmod` para quitar esos permisos. En cuanto a los permisos del usuario fénix, el ya tenía derecho de ejecución, lectura y escritura, por tanto no tuve que cambiar algo.

**En conclusión**, cambié varios permisos para que coincidiera con el nivel de autorización que la empresa requería para los archivos y directorios que se encontraban dentro del directorio projects. Lo primero fue utilizar ls -la para verificar los permisos dentro del directorio, con esta información solventé los pasos siguientes. Por último usé el comando `chmod` para cambiar los permisos de archivos y directorios.



