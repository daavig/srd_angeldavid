
<center>

# Phplists


</center>

***Nombre:*** Angél David González Quintana y Ayoze Hernández Díaz
***Curso:*** 2º de Ciclo Superior de Administración de Sistemas Informáticos en Red.

### ÍNDICE

+ [Comprobaciones previas](#id1)
+ [Instalación de Phplist](#id2)
+ [Configuración de Phplist](#id3)
+ [Creación de usuarios](#id4)
+ [Páginas de inscripción](#id5)
+ [Iniciar una campaña](#id6)

#### ***Comprobaciones previas***. <a name="id1"></a>
Para la practica necesitaremos los servicios y utilidades de:

* **Apache2**
* **Php**
* **PhpmyAdmin**

Comprobamos que tenemos los componentes instalados.

![](./img/01.png)

#### ***Instalación de Phplist***. <a name="id2"></a>

Descargamos el paquete de **phplist**.

![](./img/02.png)

Ahora descomprimimos el paquete descargado en la ruta /var/www y se nos genera la carpeta **phplist-3.6.6**.

![](./img/03.png)

Vemos el contenido de este direcotorio y movemos la  carpeta **/var/www/phplist-3.6.6/public_html/lists** a **/var/www** como se muestra en las 2 siguientes imágenes.

![](./img/04.png)

![](./img/05.png)

Entramos en la carpeta y vemos que el contenido de esta está ahí.

![](./img/06.png)

Editamos el fichero ***config.php*** situado en **/var/www/lists/config/** y cambiamos los siguientes campos:

* **$database_name** = 'phplist'
* **$database_user** = 'phpadmin'
* **$database_password** = 'David2001'

![](./img/07.png)

#### ***Configuración de Phplist***. <a name="id3"></a>

Accedemos a **localhost/list/admin** a través de un navegador. para configurar el servicio.

![](./img/08.png)

Introducimos los datos que nos solicitan como:

* Nombre.
* Nombre de la empresa u organización.
* Correo de contacto.
* Contraseña para poder entrar.

![](./img/09.png)

Continuamos y vemos que la base de datos se empieza a configurar.

![](./img/10.png)

Nos saldrá el siguiente panel indicando que puntos de la configuración han resultado exitosos y cuales todavía no han sido realizados.

#### ***Creación de usuarios***. <a name="id4"></a>

![](./img/11.png)

Ahora accedemos a la página principal de administración y listamos todos los usuarios y suscriptores.

![](./img/12.png)

Vamos a añadir un usuario a mitad de la pantalla a la derecha.

![](./img/13.png)

Añadimos su información personal y creamos otro más de la misma manera.

![](./img/14.png)

![](./img/15.png)

Ahora podemos ver en el mismo apartado los suscriptores que tenemos

![](./img/16.png)

Ahora accedemos a **Subscribers>List of lists** y añadimos una lista.

![](./img/17.png)

Llamaremos a la lista socios y podemos añadirle tanto descripción como orden de importancia de la lista.

![](./img/18.png)

Ahora añadimos miembros a la lista como se muestra en las siguientes imágenes.

![](./img/19.png)

Aquí comprobamos los miembros pertenecientes a la lista.

![](./img/20.png)

Ahora en esta nueva pestaña que se ha abierto podemos importar suscriptores a la lista de socios

![](./img/21.png)

Para añadirlos debemos de escribir sus correos en la area de texto designada para ello, luego presionamos en el botón inferior que dice **Import emails**

![](./img/22.png)

Ahora vemos que tenemos como miembros de la lista a Antonio y a Hector.

![](./img/23.png)

En la página de **list of lists** o **La lista de las listas** vemos que la lista de socios ahora tiene el número 2 que representa a Hector y Antonio.

![](./img/24.png)

#### ***Páginas de inscripción***. <a name="id5"></a>

Ahora nos dirigimos al panel lateral izquierdo y buscamos el apartado de configuración y entramos.

![](./img/25.png)

Nos aparecen varias secciones en esta página, siendo la primera una con configuración general como detalles sobre la cabecera, la introducción o el pié de página que se mostrarán en las páginas de inscripción, el idioma de la página o el título.

![](./img/26.png)

La siguiente sección nos permite editar que listas queremos que se muestren en la página de inscripción

![](./img/27.png)

La siguiente permite editar el mensaje que le llega a los usuarios una vez se suscriben.

![](./img/28.png)

Algo así vería alguien que se quiera suscribir

![](./img/29.png)

#### ***Iniciar una campaña***. <a name="id6"></a>

Nos dirigimos al panel izquierdo, a la sección de **campañas** al apartado de **Gestionar las plantillas de las campañas** e importamos una plantilla del sistema.

![](./img/30.png)

Cogemos un valor por defecto.

![](./img/31.png)

Ahora podemos ver que ha sido añadida.

![](./img/32.png)

Ahora en el **listado de campañas** podemos inciar una campaña nosotros mismos.

![](./img/33.png)

Para crear una campaña debemos de configurar 5 pasos:

#### **Paso 1**

Debemos de rellenar los campos requerido:

  * Asunto
  * Remitente
  * Contenido

![](./img/34.png)

#### **Paso 2**

En el segundo paso podemos cambiar el formato del mensaje que les llegará a los usuarios y cambiar los siguientes aspectos:

* Titulo de la campaña.
* Formato (**HTML o texto**).
* Personas a las que se les enviará.

![](./img/35.png)

#### **Paso 3**

Aquí editaremos las fechas de retención de la campaña y cuando se detendrá el envió de esta campaña a los correos de los usuarios.

![](./img/36.png)

#### **Paso 4**

Aquí podemos añadir listas enteras de usuarios a los que enviarles la campaña

![](./img/37.png)

#### **Paso 5**

Aquí podemos añadir un correo al que notificar tanto el inicio de la campaña como el fin, se le puede añadir datos estadisticos de la campaña, como cuantas veces se hizo click en ella.

![](./img/38.png)

#### **Resultado**

Ahora en el listado de campañas activas se puede ver la campaña que acabamos de crear

![](./img/39.png)
