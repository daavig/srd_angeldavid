# Mensajería Instantánea - Windows
##### Trabajo elaborado por Ayoze Hernández y Ángel David González


En esta práctica aprenderemos a instalar y configurar un servidor de mensajería instantánea en Windows Server 2016.

---

## Índice:

* [1. Servidor OpenFire](#1)

  * [1.1. Instalación](#1.1)

  * [1.2. Configuración](#1.2)

* [2. Cliente Spark](#2)

  * [2.1. Instalación](#2.1)

  * [2.2. Acceso administrador](#2.2)

  * [2.3. Configuración](#2.3)

  * [2.4. Acceso cliente](#2.4)

  * [2.5. Realizar comunicación administrador - usuario](#2.5)

---

## 1. Servicio OpenFire <a id="1"></a>

### 1.1. Instalación <a id="1.1"></a>

Para empezar con esta práctica, vamos a [descargar](https://www.igniterealtime.org/downloadServlet?filename=openfire/openfire_4_7_0_x64.exe) e instalar el servidor OpenFire. Al instalarlo nos aparecerá el siguiente mensaje:

![](./img/01.png)

Esto quiere decir que necesitamos instalar Java en nuestro equipo, por lo que vamos a la [páginea web oficial](https://www.java.com/es/download/) y lo [descargamos](https://javadl.oracle.com/webapps/download/AutoDL?BundleId=245807_df5ad55fdd604472a86a45a217032c7d):

![](./img/02.png)

Instalamos:

![](./img/03.png)

Y una vez instalado Java, volvemos a instalar OpenFire. Seguiremos los siguientes pasos:

* Seleccionamos el idioma:

  ![](./img/04.png)

* Saltamos la bienvenida:

  ![](./img/05.png)

* Leemos y aceptamos la licencia:

  ![](./img/06.png)

* Ponemos ruta de instalación:

  ![](./img/07.png)

* Creamos carpeta en el menú inicio (opcional):

  ![](./img/08.png)

* Esperamos a la instalación:

![](./img/09.png)

Con esto ya tendremos OpenFire instalado.

### 1.2. Configuración <a id="1.2"></a>

Vamos al navegador e introducimos la URL `127.0.0.1:9090` y nos debería aparecer la siguiente página de configuración de OpenFire:

![](./img/10.png)

Seleccionamos el lenguaje en Español y configuramos el servidor con las siguientes propiedades:

![](./img/11.png)

Seleccionamos la opción `Base de datos interna`:

![](./img/12.png)

Vamos a **phpmyadmin** y creamos un usuario ligado a la base de datos que vamos a crear:

![](./img/13.png)

Creamos la base de datos y asignamos al usuario anterior todos los permisos a dicha BD:

![](./img/14.png)

Seleccionamos la configuración de perfil por defecto:

![](./img/15.png)

Ponemos cuenta de administrador:

![](./img/16.png)

Y con eso ya tenemos OpenFire instalado y configurado.

---

## 2. Cliente Spark <a id="2"></a>

### 2.1. Instalación <a id="2.1"></a>

Ahora procedemos a descargar Spark desde la [página web oficial](https://www.igniterealtime.org/downloads/#openfire) o mediante [descarga directa](https://www.igniterealtime.org/downloadServlet?filename=spark/spark_2_9_4-with-jre.exe). Una vez descargado, seguimos los siguientes pasos de instalación:

![](./img/17.png)

* Saltamos la bienvenida:

  ![](./img/18.png)

* Seleccionamos la ruta de instalación:

  ![](./img/19.png)

* Creamos carpeta en el menú inicio (opcional):

  ![](./img/20.png)

* Seleccionamos si queremos un acceso directo o no:

  ![](./img/21.png)

* Instalamos:

  ![](./img/22.png)

* Finalizamos y ejecutamos Spark

  ![](./img/23.png)

### 2.2. Acceso administrador <a id="2.2"></a>

Nos pedirá usuario, contraseña y dominio, introducimos los datos de administrador y accedemos:

![](./img/24.png)

Podemos ver que hemos accedido correctamente:

![](./img/26.png)

### 2.3. Configuración <a id="2.3"></a>

Vamos a crear una nueva cuenta, para ello, ponemos usuario, contraseña y dominio:

![](./img/25.png)

Una vez creado, lo agregamos a nuestros contactos:

![](./img/27.png)

Finalmente modificamos el fichero `C:\Windows\Sistem32\drivers\etc\hosts` y agregamos la siguiente línea:

~~~
IP.DELA.MV.CLIENTE    Cliente             ## Poner IP del cliente y su nombre de equipo.
~~~

Debería verse así:

![](./img/28.png)

### 2.4. Acceso cliente <a id="2.4"></a>

Instalamos Spark en una MV Cliente Windows e intentamos acceder con el usuario cliente:

![](./img/29.png)

Al parecer, no hemos podido acceder ya que aparece este error tanto en el cliente como en el servidor:

![](./img/30.png)

### 2.5. Realizar comunicación administrador - usuario <a id="2.5"></a>

No se puede adelantar más...
