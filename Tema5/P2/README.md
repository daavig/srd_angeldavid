# FTP Windows y Linux


En esta práctica aprenderemos a instalar y configurar un servidor FTP tanto en un sistema operativo Windows Server como en un sistema operativo GNU-Linux -> Ubuntu

## 1. Windows

### 1.1. Instalación del servicio FTP

Para comenzar con esta práctica, vamos a instalar el servicio FTP en Windows Server. Para ello, iniciamos la MV de Windows Server y vamos a `Administrador del servidor -> Administrar -> Agregar roles y características`:

![](./img/01.png)

Ahora seguiremos los siguientes pasos:

* **Tipo de instalación:** Basada en roles o características.

  ![](./img/02.png)

* **Servidor de destino:** Seleccionamos nuestro servidor.

  ![](./img/03.png)

* **Roles de servidor:** Seleccionamos `Servidor web (IIS) -> Servidor FTP -> TODO`.

  ![](./img/04.png)

* **Progreso de la instalación:** Instalamos y esperamos.

  ![](./img/05.png)

Con estos sencillos pasos ya tendremos el servicio FTP instalado. Por supuesto, cualquier otro paso no mencionado se dejará por defecto.

### 1.2. Creación de sitios FTP

Ahora vamos a crear tres sitios web. Explicaremos que queremos de cada uno y los pasos a seguir.

Para crear un sitio web FTP debemos de ir a `Administrador del servidor -> Herramientas -> IIS`:

![](./img/06.png)

Y en `Servidor -> Sitios`, le damos clic en `Agregar sitio FTP`:

![](./img/07.png)

Una vez explicado, cada vez que mencionemos el paso de crear un nuevo sitio web, haremos estos dos sencillos pasos.

En todos los sitios web se debe poder acceder a través de las IPs del servidor y, en algún caso, de un nombre DNS ftp.tudominio.ext. Para ello, vamos a `Administrador del servidor -> Herramientas -> DNS`:

![](./img/11.png)

Y en `Servidor -> ZBD -> tudominio.ext` creamos un nuevo alias llamado `ftp`:

![](./img/12.png)

#### Sitio FTP 1

Para el primer sitio web, queremos lo siguiente:

* Debe estar asociado a la unidad `C:` completa.

* No debe permitir accesos anónimos.

* Sin uso de SSL.

* Sólo el usuario Administrador podrá acceder al sitio.

* Modos lectura y escritura.


##### Crear sitio

Vamos a IIS y le damos a crear sitio FTP. Le pondremos un nombre y la ruta de acceso será la unidad `C:\`:

![](./img/08.png)

Asignamos todas las IPs con el puerto 21 y deshabilitamos SSL:

![](./img/09.png)

Seleccionamos la autenticación básica y autorizamos solamente el acceso al usuario `Administrador` con permisos de lectura y escritura:

![](./img/10.png)

##### Acceso desde el explorador de archivos

Abrimos el explorador de archivos y en el cuadro de ruta escribimos `ftp://IP.DEL.NUESTRO.SERVER/`:

![](./img/13.png)

Nos pedirá iniciar sesión para acceder. Pondremos el usuario `Administrador` y la contraseña del mismo:

![](./img/14.png)

Comprobamos que tenemos acceso:

![](./img/15.png)

##### Acceso desde Internet Explorer

Abrimos Internet Explorer y en la URL escribimos `ftp://IP.DEL.NUESTRO.SERVER/`:

![](./img/16.png)

Nos pedirá iniciar sesión para acceder. Pondremos el usuario `Administrador` y la contraseña del mismo:

![](./img/17.png)

Comprobamos que tenemos acceso:

![](./img/18.png)

##### Acceso con otro usuario del dominio

Abrimos el explorador de archivos y en el cuadro de ruta escribimos `ftp://IP.DEL.NUESTRO.SERVER/`. Accedemos con el usuario `jorgarmor`:

![](./img/19.png)

Debería denegar el acceso ya que sólo el usuario `Administrador` tiene permiso a acceder al sitio:

![](./img/20.png)

##### Acceso desde el cliente

Abrimos una MV con Windows 10 que esté registrado en nuestro dominio y accedemos desde el explorador de archivos. Accedemos con el usuario `Administrador`:

![](./img/22.png)

Y comprobamos que podemos acceder correctamente desde el cliente:

![](./img/23.png)

Hacemos lo mismo desde el Internet Explorer:

![](./img/24.png)

Comprobamos que también tenemos acceso:

![](./img/25.png)

##### CLIENTE. Descargar e instalar WinSCP

Ahora vamos a instalar `WinSCP`. Es una herramienta que nos ortoga mayor facilidad al acceder vía FTP y otros servicios.

Podemos descargarlo mediante el [siguiente enlace](https://winscp.net/eng/download.php) o mediante [descarga directa](https://winscp.net/download/WinSCP-5.19.5-Setup.exe):

![](./img/26.png)

Una vez descargada lo ejecutamos y seguimos los siguientes pasos de instalación:

* **Acuerdo de licencia:** La leemos y seguimos aceptando los términos.

  ![](./img/27.png)

* **Tipo de instalación:** Instalación típica.

  ![](./img/28.png)

* **Cofiguración inicial:** Elegimos el que queramos.

  ![](./img/29.png)

* **Instalación:** Instalamos y esperamos.

  ![](./img/30.png)

Con estos pasos instalamos WinSCP de forma sencilla.

##### Comprobación de acceso al sitio web con WinSCP

Ejecutamos WinSCP y abrimos un nuevo sitio poniendo el protocolo FTP, sin cifrado, IP del servidor, puerto, usuario y contraseña:

![](./img/31.png)

Accedemos al servidor con el usuario `Administrador` y comprobamos que podemos ver la unidad `C:` del servidor correctamente:

![](./img/32.png)

##### Comprobación con DNS

En este caso (que es opcional), usando el registro DNS mencionado anteriormente, accedemos al sitio FTP usando el registro DNS, es decir, abrimos el navegador y escribimos `ftp://ftp.tudominio.ext/`, hacemos el inicio de sesión y comprobamos:

![](./img/33.png)

##### Sitio FTP 2

Para el segundo sitio web, queremos lo siguiente:

* Debe estar asociado al directorio `C:\inetpub\wwwroot`.

* No debe permitir accesos anónimos.

* Permitir SSL.

* Se permitirá acceso a todos los usuarios de Active Directory.

* Modos lectura y escritura.

##### Crear sitio

Vamos a IIS y le damos a crear sitio FTP. Le pondremos un nombre y la ruta de acceso será el directorio `C:\inetpub\wwwroot`:

![](./img/34.png)

Asignamos todas las IPs con el puerto 21 y permitimos SSL. Seleccionamos un certificado SSL que ya tengamos creado:

![](./img/35.png)

Seleccionamos la autenticación básica y autorizamos a todos los usuarios con permisos de lectura y escritura. Con todos nos referimos a los usuarios de Active Directory:

![](./img/36.png)

##### Acceso desde el explorador de archivos

Abrimos el explorador de archivos y en el cuadro de ruta escribimos `ftp://IP.DEL.NUESTRO.SERVER/` o `ftp://ftp.tudominio.ext/`. Nos pedirá iniciar sesión para acceder. Podemos poner cualquier usuario del AD, así que pondremos el usuario `ayogonlop` y la contraseña del mismo:

![](./img/39.png)

Comprobamos que tenemos acceso:

![](./img/40.png)

##### Acceso desde Internet Explorer

Abrimos Internet Explorer y en la URL escribimos `ftp://IP.DEL.NUESTRO.SERVER/` o `ftp://ftp.tudominio.ext/`. Nos pedirá iniciar sesión para acceder. Pondremos ahora el usuario `jorgarmor` y la contraseña del mismo:

![](./img/37.png)

Comprobamos que tenemos acceso:

![](./img/38.png)

##### Acceso con usuario fuera de Active Directory

Abrimos Internet Explorer y en el cuadro de ruta escribimos `ftp://IP.DEL.NUESTRO.SERVER/` o `ftp://ftp.tudominio.ext/`. Accedemos con el usuario local `angeldavid`:

![](./img/41.png)

Debería denegar el acceso ya que sólo los usuarios de Active Directory tienen permiso a acceder al sitio:

![](./img/42.png)

##### Acceso desde el cliente

Vamos a la MV con Windows 10 y accedemos desde el explorador de archivos. Accedemos con el usuario `alejandro`:

![](./img/43.png)

Y comprobamos que podemos acceder correctamente desde el cliente:

![](./img/44.png)

Hacemos lo mismo desde el Internet Explorer pero con el usuario `alexander`:

![](./img/45.png)

Y comprobamos que también tenemos acceso:

![](./img/46.png)

##### Comprobación de acceso al sitio web con WinSCP

Ahora abrimos WinSCP y abrimos una nueva sesión poniendo el protocolo FTP, con cifrado SSL explícito, IP del servidor, puerto, usuario de Active Directory y contraseña:

![](./img/47.png)

Nos preguntará si estamos seguros de acceder al servidor. Aceptamos y accedemos:

![](./img/48.png)

Comprobamos que podemos ver el directorio `C:\inetpub\wwwroot\` del servidor correctamente:

![](./img/49.png)

#### Sitio FTP 3

Para el tercer sitio web, queremos lo siguiente:

* Debe estar asociado a la carpeta que queramos (siempre que no sea importante).

* Debe permitir accesos anónimos.

* Sin SSL.

* Modo lectura.

##### Crear sitio

Vamos a IIS y le damos a crear sitio FTP. Le pondremos un nombre y la ruta de acceso será el directorio que queramos:

![](./img/50.png)

Asignamos todas las IPs con el puerto 21 y deshabilitamos SSL:

![](./img/51.png)

Seleccionamos la autenticación anónima y permitimos el acceso a los usuarios anónimos con permisos de lectura:

![](./img/52.png)

> ***A partir de aquí, no se ha podido avanzar más con el sitio web 3 debido a problemas con los usuarios anónimos.***

### 1.3. Habilitar varios sitios FTP simultáneamente

Anteriormente, debíamos detener un sitio web para activar otro. En este paso haremos que podamos activar y acceder a los tres sitios simultáneamente (dos, ya que el sitio web 3 no está funcional).

Para ello, vamos a `Firewall de Windows con seguridad avanzada` y en `Reglas de entrada` creamos una nueva regla:

![](./img/60.png)

Seguiremos los siguientes pasos:

* **Tipo de regla:** Puerto.

  ![](./img/61.png)

* **Protocolo y puerto:** Protocolo TCP y puertos locales del 5000 al 5010.

  ![](./img/62.png)

* **Acción:** Permitir la conexión.

  ![](./img/63.png)

* **Perfil:** Aplicar regla a todo.

  ![](./img/64.png)

* **Nombre:** Ponemos un nombre para identificar la regla.

  ![](./img/65.png)

Comprobamos que se ha creado la regla correctamente:

![](./img/66.png)

Ahora vamos a `IIS -> Servidor -> Compatibilidad con el firewall de FTP` y ponemos en el intervalo de puerto del canal de datos pondremos el rango de puertos que establecimos en la regla del firewall:

![](./img/67.png)

Ahora vamos a `Sitios`. Seleccionamos un sitio FTP y le damos a `Enlaces`:

![](./img/68.png)

Modificamos el puerto del sitio y le ponemos un puerto del 5000 al 5010:

![](./img/69.png)

Hacemos lo mismo con los otros 2 sitios FTP:

![](./img/70.png)

Vamos al equipo cliente y abrimos WinSCP. Abrimos dos sesiones con los dos sitios web FTP funcionales. Para cada sitio pondremos el puerto que le corresponde:

Sitio Web 1:

![](./img/71.png)

Sitio Web 2:

![](./img/72.png)

Con esto ya hemos conseguido abrir varios sitios FTP simultáneamente.

---

## 2. Linux

### 2.1. Instalación del servicio SSH

Para empezar con Linux, necesitaremos instalar el servicio `SSH`. Para ello, iniciamos una MV de Linux (Xubuntu) y abrimos una terminal como usuario ***root*** con el comando `sudo su`.

Instalamos el servicio con el comando `apt install ssh`:

![](./img/73.png)

Esperamos a que se instale.

### 2.2. Crear usuarios

Una vez instalado, crearemos dos usuarios con distintos permisos:

|Usuario|Grupo|
|-------|-----|
|user1|users|
|user2|root|

Para ello, usaremos el siguiente comando:

~~~
useradd -g grupo -d /home/usuario -m -s /bin/bash/ usuario
~~~

Deberían quedar así:

![](./img/74.png)

Para que el usuario `user2` tenga privilegios de usuario root, editamos el fichero `/etc/sudoers` con el comando `nano` y escribimos la siguiente línea:

~~~
user2   ALL=(ALL:ALL) ALL
~~~

Debería quedar así:

![](./img/75.png)

Cerramos sesión y accedemos con el usuario `user1`. Comprobamos que no podemos eliminar ficheros protegidos ya que no tenemos permisos:

![](./img/76.png)

Cerramos sesión y accedemos con el usuario `user2`. Comprobamos que podemos instalar algún que otro paquete:

![](./img/77.png)

### 2.3. Comprobar SSH desde el cliente

Ahora iniciamos una MV de Linux (Xubuntu) cliente, abrimos una terminal y probamos el acceso remoto con el comando `ssh user1@IP.DEL.EQUIPO.SERVIDOR`. Ponemos la contraseña del usuario `user1` y comprobamos que tenemos acceso:

![](./img/78.png)

Hacemos lo mismo con el usuario `user2`. Usamos el comando `ssh user2@IP.DEL.EQUIPO.SERVIDOR`:

![](./img/79.png)

### 2.4. Ejecutar programa desde el cliente mediante SSH

Ahora vamos a probar a ejecutar un programa del servidor (firefox) desde el cliente. Para ello, ejecutamos el comando `ssh usuario@IP.DEL.EQUIPO.SERVIDOR firefox`:

![](./img/97.png)

Como se puede ver, nos sale un error mencionando que no se muestra una pantalla específica y no podemos ejecutar el programa.

### 2.5. Instalación del paquete proftpd

Ahora vamos a instalar el paquete `proftpd`. Para ello, vamos a la MV de Linux Server y ejecutamos el comando `apt install proftpd`:

![](./img/80.png)

Nos preguntará si se ejecutará desde inetd o independientemente. Nosotros seleccionamos la segunda opción:

![](./img/81.png)

Una vez instalado, comprobamos la versión con el comando `proftpd --version`:

![](./img/82.png)

Finalmente comprobamos si está activado con el comando `systemctl status proftpd`:

![](./img/83.png)

### 2.6. Configurar proftpd

Para configurar proftpd, necesitaremos modificar el fichero de configuración `/etc/proftpd/proftpd.conf` con el comando `nano` y modificaremos lo siguiente:

![](./img/84.png)

### 2.7. Conectar al servicio FTP (servidor/cliente)

#### Desde el servidor (Local)

Para probar el acceso FTP de manera local, simplemente ejecutaremos el comando `ftp 127.0.0.1` y pondremos el usuario y contraseña:

* **user1:**

  ![](./img/85.png)

* **user2:**

  ![](./img/86.png)

#### Desde el cliente (Remoto)

Para probar el acceso FTP de manera remota, ejecutamos el comando `ftp IP.DEL.EQUIPO.SERVIDOR` desde el cliente y pondremos el usuario y contraseña:

* **user1:**

  ![](./img/87.png)

* **user2:**

  ![](./img/93.png)

### 2.8. Comprobación de operaciones FTP desde el cliente

Ahora vamos a probar operaciones FTP desde el cliente. En el servidor crearemos los ficheros `server-us1.txt` (desde el usuario `user1`) y `server-us2.txt` (desde el usuario `user2`). En el cliente crearemos los ficheros `cliente-us1.txt` y `cliente-us2.txt`.

#### user1

Accedemos al servidor mediante FTP:

![](./img/87.png)

Comprobamos la lista de directorios con el comando `dir`:

![](./img/88.png)

Obtenemos el fichero `server-us1.txt` del servidor con el comando `get`:

![](./img/89.png)

Comprobamos en el cliente que tenemos el fichero:

![](./img/90.png)

Subimos el fichero del cliente `cliente-us1.txt` para tenerlo en el servidor con el comando `put`:

![](./img/91.png)

Comprobamos desde el servidor que hemos obtenido el fichero:

![](./img/92.png)

#### user2

Accedemos al servidor mediante FTP y comprobamos la lista de directorios con el comando `dir`:

![](./img/93.png)

Subimos el fichero del cliente `cliente-us2.txt` para tenerlo en el servidor con el comando `put`:

![](./img/96.png)

Comprobamos desde el servidor que se ha subido el fichero correctamente:

![](./img/98.png)

Y obtenemos el fichero `server-us2.txt` del servidor con el comando `get`. Comprobamos con el comando `dir`.

> ***He perdido la última imagen.***
