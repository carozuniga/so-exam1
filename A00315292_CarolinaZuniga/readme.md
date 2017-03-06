Universidad ICESI
## Informe Examen 1
**Nombre:**  Carolina Zúñiga

**Código:**  A00315292

**Url Repositorio**: https://github.com/ICESI-Training/so-exam1/A00315292_CarolinaZuniga

### Solución a las preguntas

3- Los 5 retos escogidos fueron los siguientes:

- current_working_directory/

Este reto consiste en imprimir el directorio actual de trabajo, para lo cual se utiliza el comando pwd.
ejemplo:

![][1]

En este caso despues de ejecutar el comando vemos que nos encontramos en el directorio /root/curl-7.32.0

- print_file_contents/ 

Este reto consiste en imprimir el contenido de un archivo que se encuentre en el directorio actual, para lo cual se utiliza el comando cat..
ejemplo:

![][2]

Para este ejemplo cree un archivo llamado ejemplo.txt con el comando vi, y para poder verlo utilicé el comando cat, que me permite ver el contenido de un archivo.

- find_string_in_a_file/

Este reto consiste en imprimir todas las lineas de un determinado archivo que contengan un string especificado, para esto se emplea el comando grep.
ejemplo:

![][3]

Usando el mismo archivo del ejemplo anterior (ejemplo.txt), se empleó el comando para imprimir todas las lineas que tuvieran "de". Empleando el comando grep lo podemos solucionar siguiendo la siguiente estructura:
grep cadena_de_caracteres archivo.

- simple_sort/

Este reto consiste en imprimir el contenido de un archivo de forma ordenada, para este reto se usó el comando sort.
ejemplo:

![][4]

Para el ejemplo, creé un archivo llamado orden.txt el cual tiene los numeros desordenados del 1 al 5, al usar el comando sort orden.txt, se observa cómo el contenido del archivo ahora se muestra de forma ordenada.

- print_number_sequence/

Este reto consiste en imprimir los numeros del 1 al 100 separados por espacios. Para esto empleé el comando echo y seq.
ejemplo:

![][5]

Con esta línea se imprime en 1 sola línea el comando seq 100, este comando imprime los números del 1 hasta el número que escribamos como argumento.

4- Para resolver este punto, primero cree un archivo llamado list.txt que contiene 2 direcciones ip, una dirección por línea. Estas direcciones ip son de las otras maquinas virtuales de CentOS 7, ambas contienen el usuario operativos con contraseña operativos.

![][10]

el script que descarga de forma remota un libro desde las distintas maquinas es el siguiente:

![][9]

la primera línea input, tiene la dirección en la que se encuentra el archivo de list.txt mencionado anteriormente. Después se hace un while que lee el archivo línea por línea hasta que se acaba. Cada línea se almacena en la variable line.

Para ingresar a la maquina usé el protocolo ssh, y como en este caso la contraseña para todas las maquinas es la misma (operativos), empleé la herramienta sshpass para automatizar este proceso y no tener que escribir todas las contraseñas manualmente.

sshpass se puede obtener en la maquina con el comando yum install sshpass, y se encuentra en el repositorio EPEL, si no se cuenta con este repositorio, lo debemos instalar antes con el siguiente comando: yum install epel-release.

Después de ingresar la contraseña entre comillas en el argumento de -p, se procede a usar el comando ssh que me permite hacer una conexión remota. Para emplearlo se usa el siguiente formato:

ssh usuario@ip [comandos]

Usuario va a ser reemplazado por operativos, que es el usuario al que queremos acceder, la ip es reemplazada por la línea actual del archivo mencionado anteriormente. Por último escribimos los comandos que queremos ejecutar en la maquina remota, empezando por cd /tmp para ubicarnos en el directorio destino. de forma siguiente se encuetra pwd que nos imprime el directorio actual, para poder visualizar que efectivamente nos encontramos en el directorio /tmp.

Por último utilizamos el comando wget (que debe estar instalado en las demás maquinas), para descargar el libro de alice in worderland de la pagina www.gutenberg.org ubicado en la url que tiene como argumento.

Para poder correr este script debemos modificarle los permisos con chmod (chmod 700 script3.sh). Al ejecutar el script se obtiene el siguiente resultado:

![][6]

En esta captura se puede ver el ingreso a las 2 maquinas que tiene en el list.txt , en cada una de ellas se ubica en el directorio /tmp y descarga el libro, dejandolo en un archivo llamado pg19033.txt


![][7]

En esta captura se observa la primera maquina, con dirección ip 192.168.0.32, ingresamos al usuario operativos, nos ubicamos en el directorio /tmp y podemos visualizar que dentro de ella se encuentra el libro.

Lo mismo sucede con la siguiente maquina en la lista que tiene como dirección ip la 192.168.192.130:

![][8]

Finalmente como constancia observamos el contenido del archivo descargado pg19033.txt para verificar que sí es el libro:

![][16]


5- Para crear un contenedor de debian en CentOS7 se deben emplear los siguientes pasos:

  - Tener instalado el repositorio EPEL y como se mencionó en el punto anterior, lo podemos descargar e instalar usando el siguiente comando:
yum install epel-release

  - Instalar el lenguaje intérprete Perl y los paquetes debootstrap:
yum install debootstrap perl libvirt

  - Instalar LXC:
yum install lxc lxc-templates

  - Comprobar que los servicios LXC  y libvirt estén corriendo así:
![][12]

  - Crear el contenedor LXC con el siguiente comando:
lxc-create -n nombre_contenedor -t tipo

En este caso el nombre será mycont y el tipo debian. Al finalizar obtenemos un mensaje como el siguiente en el cual nos dicen la contraseña del usuario root:
![][13]

- Para ver los contenedores que tenemos nos dirigimos al directorio /var/lib/lxc
![][14]

- Para iniciar y entrar al contenedor utilizamos el comando:
lxc-start -n nombre
![][15]

En esta captura podemos ver que ya tenemos acceso a nuestro contenedor. 

- Para apagarlo solo es necesario el comando: poweroff


### Referencias
- http://docs.oracle.com/cd/E19620-01/805-7644/6j76klop3/index.html
- https://www.lifewire.com/uses-of-linux-seq-command-4011324
- https://support.rackspace.com/how-to/install-epel-and-additional-repositories-on-centos-and-red-hat/
- https://www.cyberciti.biz/faq/unix-howto-read-line-by-line-from-file/
- https://www.cyberciti.biz/faq/noninteractive-shell-script-ssh-password-provider/
- http://www.shellhacks.com/en/Running-Commands-on-a-Remote-Linux-Server-over-SSH
- http://www.tecmint.com/install-create-run-lxc-linux-containers-on-centos/

[1]: Images/1.PNG
[2]: Images/2.PNG
[3]: Images/3.PNG
[4]: Images/4.PNG
[5]: Images/5.PNG
[6]: Images/6.PNG
[7]: Images/7.PNG
[8]: Images/8.PNG
[9]: Images/9.PNG
[10]: Images/10.PNG
[11]: Images/11.PNG
[12]: Images/12.PNG
[13]: Images/13.PNG
[14]: Images/14.PNG
[15]: Images/15.PNG
[16]: Images/16.PNG
