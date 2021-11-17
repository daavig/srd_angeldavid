# IIS Servidor Web avanzado - PHP, MySQL, phpMyAdmin, FTP y Drupal

Vamos a realizar las instalaciones y configuraciones necesarias para obtener un Servidor Web con
soporte PHP y accesos a bases de datos relacionales, acceso FTP y gestor de bases de datos. Sobre
este servidor, podremos realizar instalaciones de aplicaciones integradas (CMS, e-commerce, etc)
desde el propio servidor o en modo remoto desde un cliente W7.

## 1. Instalar PHP

Para empezar vamos instalar PHP. Para ello, vamos al [siguiente enlace](https://windows.php.net/download/) y le damos clic a `Archives -> archives`:

![1](./img/01.png)

Nos saldrán muchísimas opciones. Nosotros elegiremos la versión `PHP 5.3.9 VC9 Non Thread-Safe (con IIS Fast CGI)` o podemos darle clic directamente al [siguiente enlace](https://windows.php.net/downloads/releases/archives/php-5.3.9-nts-Win32-VC9-x86.msi) para descargarlo:

![1](./img/02.png)

Una vez descargado, también necesitaremos descargar e instalar WebPI (versión 5.0). Para ello, vamos al [siguiente enlace](https://www.microsoft.com/web/downloads/platform.aspx) y le damos al paquete x64 ([descarga directa](https://go.microsoft.com/fwlink/?LinkId=287166)):

![1](./img/03.png)

Lo ejecutamos:

![1](./img/04.png)

Aceptamos los términos de licencia:

![1](./img/05.png)

Y se instalará:

![1](./img/06.png)

Ahora vamos a `Administrador del servidor -> Administrar -> Agregar roles...` y agregamos la característica `CGI` situada en `Servidor Web (IIS) -> Servidor web -> Desarrollo de aplicaciones`:

![1](./img/07.png)

Instalamos la característica:

![1](./img/08.png)

Una vez finalizada la Instalación, ejecutamos el paquete PHP:

![1](./img/09.png)

Seguiremos los siguientes pasos:

* **Términos de licencia:** Las aceptamos.

  ![1](./img/10.png)

* **Directorio de destino:** El que queramos (es recomendable el que nos salga por defecto).

  ![1](./img/11.png)

* **Configuración del servidor web:** IIS FastCGI.

  ![1](./img/12.png)

* **Elementos a instalar:** Seleccionamos todos.

  ![1](./img/13.png)

Finalmente seguimos e instalamos.

---

## 2. Comprobación PHP

Debemos comprobar que la instalación funcionó y que el PHP funciona correctamente. Para ello, primero vamos a `Administrador del servidor -> Herramientas -> IIS -> Server -> Documentos predeterminados`:

![2](./img/14.png)

Y verificamos que el documento `index.php` está en la lista.

![2](./img/15.png)

Como está en la lista, vamos a colocar un fichero `index.php` en el sitio web destinado a gestionar el CMS Drupal (en nuestro caso, `www.repcan.com` o `..\repcan\principal`). Le pondremos el siguiente código al fichero:

~~~
<?php phpinfo(); ?>
~~~

![2](./img/16.png)

Como tenemos un fichero `index.html`, nos puede ocasionar problemas, simplemente lo movemos a la carpeta `img` que teníamos creada, borrarlo, cambiarle de nombre, etc..., mientras no nos ocasione problemas:

![2](./img/17.png)

Finalmente abrimos un navegador y en el cuadro de búsqueda pondremos `www.repcan.com` y debería salir lo siguiente:

![2](./img/18.png)

Si nos sale como en la imagen anterior, entonces hemos realizado el proceso correctamente.

---

## 3. Instalar MySQL

### 3.1. Instalar .NET Framework

Antes de instalar MySQL, debemos instalar `.NET Framework 4.0`. Para ello, podemos ir al [siguiente enlace](https://www.microsoft.com/es-es/download/details.aspx?id=17851), seleccionar el idioma y descargarlo ([descarga directa en Español](https://www.microsoft.com/es-es/download/confirmation.aspx?id=17851)):

![3-1](./img/20.png)

Lo ejecutamos e instalamos. En mi caso, ya tenía la versión que necesitamos, por lo que si pasa lo mismo, cerramos ya que no nos dejará hacer nada:

![3-1](./img/21.png)

### 3.2. Instalar MySQL y complementos

Ahora sí que vamos a instalar MySQL (versión 5.7.35 ). Para ello, vamos a la página de [MySQL](https://downloads.mysql.com/archives/installer/) y seleccionar la versión y el sistema operativo que se ve en la siguiente imagen ([descarga directa](https://downloads.mysql.com/archives/get/p/25/file/mysql-installer-community-5.7.35.0.msi)):

![3-2](./img/22.png)

Una vez descargado, procedemos a los pasos de instalación:

* **Tipo de configuración:** Desarrollador predeterminado.

  ![3-2](./img/23.png)

* **Comprobación de requisitos:** Dar clic en `Ejecutar`.

  ![3-2](./img/24.png)

* **Programas:** Al darle a ejecutar, se descargarán algunos programas. Nosotros los instalamos.

  ![3-2](./img/25.png)

  ![3-2](./img/26.png)

  Deberían estár todos correctos. Seguimos:

  ![3-2](./img/27.png)

* **Instalación:** Dar clic en `Ejecutar`.

  ![3-2](./img/28.png)

  Se instalarán todos los programas que nos aparecerá en pantalla en segundo plano. Una vez finalizado, seguimos:

  ![3-2](./img/29.png)

* **Configuración del producto:** Hay que configurar los productos que aparecen. Seguimos.

  ![3-2](./img/30.png)

##### MySQL Server

* **Tipo y redes:** Lo dejamos por defecto.

  ![3-2](./img/31.png)

* **Roles y cuentas:** Ponemos contraseña `Root` y agregamos un usuario, con el rol de administrador de base de datos y también con contraseña.

  ![3-2](./img/32.png)

  Debería quedar así:

  ![3-2](./img/33.png)

* **Servicio Windows:** Dejamos lo que se muestra en la siguiente imagen.

  ![3-2](./img/34.png)

* **Aplicar configuración:** Le damos clic en `Ejecutar`.

  ![3-2](./img/35.png)

  Finalizamos:

  ![3-2](./img/36.png)

##### MySQL Router

* **Configuración del producto:** Configuramos ahora MySQL Router. Seguimos.

  ![3-2](./img/37.png)

* **Configuración del router MySQL:** Lo dejamos por defecto.

  ![3-2](./img/38.png)

##### Samples and Examples

* **Conectar al servidor:** Nos conectamos al servidor con el usuario root creado anteriormente y le damos clic a `Comprobar`.

  ![3-2](./img/39.png)

* **Aplicar configuración:** Le damos clic a `Ejecutar`.

  ![3-2](./img/40.png)

  Finalizamos:

  ![3-2](./img/41.png)

Finalmente nos volverá la pantalla de configuración de producto pero ya están los productos instalados:

![3-2](./img/42.png)

Finalmente finalizamos el proceso de instalación de MySQL:

![3-2](./img/43.png)

---

## 4. Instalar phpMyAdmin

En este paso vamos a instalar phpMyAdmin para nuestros sitios web gestionados por IIS.

Lo primero que haremos es ir a la página web de [phpMyAdmin](https://www.phpmyadmin.net/files/) y descargar la versión 4.4.15.10 ([descarga directa](https://files.phpmyadmin.net/phpMyAdmin/4.4.15.10/phpMyAdmin-4.4.15.10-all-languages.zip)):

![4](./img/44.png)

Creamos una carpeta en nuestra ruta de sitios web para phpMyAdmin y exportamos el fichero que hemos descargado en ella (C:\repcan\phpMyAdmin):

![4](./img/45.png)

Vamos a `Administrador del servidor -> Herramientas -> DNS -> Server -> ZBD -> miEmpresa` y creamos un nuevo dominio. Le pondremos el nombre de phpMyAdmin:

![4](./img/46.png)

Agregamos el ***Host*** del servidor y el ***Alias*** hacia el host creado:

![4](./img/47.png)

Ahora vamos a `IIS -> Server -> Certificados del servidor` y le damos a `Crear certificado autofirmado`. Le ponemos un nombre y lo crearemos para hospedaje de sitios web:

![4](./img/48.png)

Ahora creamos un nuevo sitio web con los siguientes parámetros:

![4](./img/49.png)

Seleccionamos el sitio web y le damos a `Enlaces`. Agregamos el enlace http:

![4](./img/50.png)

Finalmente vamos a comprobarlo desde el navegador. Para ello, abrimos un navegador y en el cuadro de búsqueda pondremos `https://www.phpmyadmin.repcan.com` y si todo lo hemos hecho bien, debería salir el login de phpMyAdmin. Ponemos usuario root y contraseña:

![4](./img/51.png)

Y comprobamos que podemos acceder correctamente:

![4](./img/52.png)

---

## 5. Filezilla FTP Server

### 5.1. Instalación

Para terminar con el servidor, vamos a instalar ahora Filezilla. Para ello, vamos a descargar Filezilla Server desde el [siguiente enlace](https://filezilla-project.org/download.php?type=server) ([descarga directa](https://dl2.cdn.filezilla-project.org/server/FileZilla_Server_1.1.0_win64-setup.exe?h=Z54Fes499qVtfa4DZM2rjw&x=1637180983)):

![5-1](./img/53.png)

Una vez descargado procedemos a los pasos de instalación:

* **Términos de licencia:** Las leemos y aceptamos.

  ![5-1](./img/54.png)

* **Selección de componentes:** Los seleccionamos todos.

  ![5-1](./img/55.png)

* **Ubicación de instalación:** La que queramos (es recomendable usar la ubicación por defecto).

  ![5-1](./img/56.png)

* **Ajustes de servidor:** Lo instalamos como un servicio que se escucha por el puerto 14148 y ponemos contraseña de administrador.

  ![5-1](./img/57.png)

* **Ajustes de administrador:** Lo dejamos por defecto.

  ![5-1](./img/58.png)

* **Instalación:** Esperamos a la instalación y al completarse cerramos.

  ![5-1](./img/59.png)

Una vez instalado, podremos conectarnos:

![5-1](./img/60.png)

### 5.2. Usuario y permisos

Una vez nos conectamos, vamos a crear un usuario. Para ello, vamos a `Servidor -> Configurar...`:

![5-2](./img/61.png)

Vamos a `Usuarios` y creamos el usuario `ftpuser` con una contraseña a nuestro gusto y su dirección nativa será la que usamos para el CMS Drupal (C:\repcan\principal). Finalmente le pondremos los permisos de escritura clicando la opción `Escribible`:

![5-2](./img/62.png)

### 5.3. Crear registro DNS

Finalmente vamos a `Administrador del servidor -> DNS -> Server -> ZBD -> miEmpresa` y creamos un nuevo alias con el nombre `ftp`:

![5-3](./img/63.png)

Debería quedar así:

![5-3](./img/64.png)

---

## 6. Comprobación desde el cliente

Ahora todo lo que hagamos (salvo que se mencione) se realizará desde el equipo cliente.

### 6.1. Comprobación de acceso a phpMyAdmin

Primero comprobamos que podemos acceder desde el cliente al phpMyAdmin del servidor. Para ello, abrimos un navegador y en el cuadro de búsqueda pondremos `https://www.phpmyadmin.repcan.com`:

![6-1](./img/65.png)

Ponemos usuario y contraseña y comprobamos que podemos acceder correctamente:

![6-1](./img/66.png)

### 6.2. Descargar CMS Drupal

Vamos a descargar Drupal. Necesitamos la versión 6.38, por lo que accederemos a él desde el [siguiente enlace](https://www.drupal.org/drupal-6.38-release-notes) ([descarga directa](https://ftp.drupal.org/files/projects/drupal-6.38.zip)):

![6-2](./img/67.png)

Una vez descargado lo exportamos:

![6-2](./img/68.png)

### 6.3. Comprobación de acceso al sitio FTP

Comprobamos el acceso al servidor FTP del servidor. Para ello, abrimos un navegador y en el cuadro de búsqueda pondremos `ftp://ftp.repcan.com`. Si sale bien, pondremos el usuario FTP `ftpuser` y su contraseña:

![6-3](./img/69.png)

Si hemos puesto el usuario y la contraseña correctamente, debería resolver la página así:

![6-3](./img/70.png)

### 6.4. Instalar Filezilla FTP Client

Vamos a instalar el cliente FTP de Filezilla. Para ello, vamos a descargar Filezilla Client desde el [siguiente enlace](https://filezilla-project.org/download.php?platform=win64) ([descarga directa](https://download.filezilla-project.org/client/FileZilla_3.56.2_win64_sponsored-setup.exe)):

![6-4](./img/71.png)

Una vez descargado procedemos a los pasos de instalación:

* **Opciones de instalación:** Lo queremos sólo para el usuario que estamos usando.

  ![6-4](./img/72.png)

* **Selección de componentes:** Los seleccionamos todos.

  ![6-4](./img/73.png)

* **Ubicación de instalación:** La que queramos (es recomendable usar la ubicación por defecto).

  ![6-4](./img/74.png)

### 6.5. Descomprimir y subir archivos Drupal

Una vez instalado, podremos conectarnos al servidor desde el Filezilla Client:

![6-5](./img/75.png)

Abrimos nuestra carpeta descomprimida Drupal y la arrastramos hacia el directorio `C:\repcan\principal` del servidor:

![6-5](./img/76.png)

Si todo sale bien, debería salir en `Transferencias satisfactorias`:

![6-5](./img/77.png)

Para comprobar que se ha pasado dicha carpeta, abrimos un navegador y en el cuadro de búsqueda pondremos `ftp://ftp.repcan.com` y comprobamos que están todos los ficheros Drupal:

![6-5](./img/78.png)

### 6.6. Crear base de datos y usuario en phpMyAdmin

Volvemos al navegador y accedemos al servidor phpMyAdmin. Una vez dentro, vamos a `Bases de datos` y creamos una nueva base de datos con el nombre `cms` y cotejamiento `utf8_spanish2_ci`:

![6-6](./img/79.png)

Ahora vamos a `Usuarios` y le damos a `Agregar usuario`:

![6-6](./img/80.png)

Le ponemos el nombre `cms`, le ponemos contraseña y le damos todos los privilegios:

![6-6](./img/81.png)

Pero queremos que tenga todos los privilegios sobre la base de datos `cms`. Para ello, vamos a `Usuarios -> cms -> Editar los privilegios`:

![6-6](./img/82.png)

Seleccionamos la base de datos `cms`:

![6-6](./img/83.png)

Le damos todos los privilegios y guardamos los cambios:

![6-6](./img/84.png)

Debería actualizarse los privilegios correctamente:

![6-6](./img/85.png)

### 6.7. Instalar CMS Drupal

Finalmente vamos a instalar Drupal desde el navegador. Para ello, abrimos un navegador y en el cuadro de búsqueda pondremos `https://www.repcan.com/drupal`y seguiremos los siguientes pasos de instalación:

* Seleccionamos otro lenguaje que no sea el Inglés:

  ![6-7](./img/86.png)

* No podremos cambiar ahora el idioma, pero lo podemos hacer luego con un paquete de idioma:

  ![6-7](./img/87.png)

* Instalamos Drupal en Inglés. Los primeros requisitos son que debemos cambiar de nombre un fichero y darle al mismo permisos:

  ![6-7](./img/88.png)

* Para el fichero, vamos a `C:\miEmpresa\principal\drupal\sites\default` y localizamos el fichero `default.settings.php`:

  ![6-7](./img/89.png)

* Modificamos el nombre y lo dejamos como `settings.php`:

  ![6-7](./img/90.png)

* Le damos clic derecho al fichero y le damos a `Propiedades -> Seguridad -> Editar...`, seleccionamos los usuarios del dominio y les damos permisos de control total:

  ![6-7](./img/91.png)

* Reiniciamos el servidor y el cliente por si acaso. Luego al regresar a la página nos saldrá la configuración de la base de datos. Si ponemos la base de datos `cms` con el usuario `cms` se reinicia la misma página, por lo que tenemos que editar el fichero anterior `settings.php`:

  ![6-7](./img/92.png)

* Editamos el fichero y sustituimos la línea 91 y pondremos lo siguiente:
  ~~~
  $db_url = 'mysql://usuario:contraseña@host/basededatos';
  ~~~

  Debería quedar así:

  ![6-7](./img/93.png)

* Ponemos nuestro sitio web y un correo electrónico, además de una cuenta de administrador Drupal con contraseña:

  ![6-7](./img/94.png)

* Establecemos zona horaria:

  ![6-7](./img/95.png)

Y ya tendríamos instalado Drupal desde el navegador:

  ![6-7](./img/96.png)

### 6.8. Configuración y creación del sitio Drupal

Finalmente, vamos a crear y configurar el sitio Drupal. Para ello, instalaremos el módulo `gtranslate` para poder cambiar idiomas, instalamos los temas `Marinelli`, `Zen` y `Fusion`, creamos una página de contenido y creamos un menú Primary Links (ya viene creado por defecto) y lo colocamos como bloque.

En mi caso, he instalado el módulo y los temas, pero sólo creé una página de prueba con el tema Fusion:

![6-8](./img/97.png)
