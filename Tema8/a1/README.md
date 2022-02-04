# Instalación y Configuración de un Servidor Streaming Multimedia - Windows 2016

---

## Índice


* [1. Instalación del servicio web (IIS)](#1)

* [2. Descarga e instalación de Unreal Media Server](#2)

* [3. Comprobación del vídeo de prueba](#3)

* [4. Creación de carpeta virtual](#4)

* [5. Comprobación](#5)

---

### 1. Instalación del servicio web (IIS) <a id="1"></a>

Para comenzar esta práctica, vamos a nuestra MV de Windows Server 2016 y accedemos a `Administrador del servidor -> Administrar -> Agregar roles y características`:

![](./img/01.png)

Ahora seguiremos los siguientes pasos:

* **Tipo de instalación:** Basada en roles.

  ![](./img/02.png)

* **Servidor de destino:** Seleccionamos nuestro servidor.

  ![](./img/03.png)

* **Roles del servidor:** Seleccionamos `Servidor web (IIS)`.

  ![](./img/04.png)

El resto de opciones los dejamos por defecto, seguimos e instalamos (en mi caso, ya lo tenía instalado por lo que no puedo mostrar más).

---

### 2. Descarga e instalación de Unreal Media Server <a id="2"></a>

Ahora vamos a la página web oficial de [Unreal Media Server](http://umediaserver.net/umediaserver/download.html) y descargamos el programa de 64 bits. [Descarga directa](http://umediaserver.net/bin/UMediaServer(x64).zip):

![](./img/05.png)

Una vez descargado lo descomprimimos:

![](./img/06.png)

Y vemos que solo tiene el instalador, por lo que lo ejecutamos:

![](./img/07.png)

Nos preguntará si queremos ejecutar el archivo, por lo que aceptamos:

![](./img/08.png)

Y se abrirá una ventana del instalador dándonos la bienvenida, seguimos:

![](./img/09.png)

Leemos y aceptamos los términos de licencia:

![](./img/10.png)

Seleccionamos la ruta de instalación:

![](./img/11.png)

Y esperamos a que se instale:

![](./img/12.png)

Una vez finalizado, ya tenemos Unreal Media Server instalado.

---

### 3. Comprobación del vídeo de prueba <a id="3"></a>

Ejecutamos el programa y vemos que tiene una carpeta de recursos con dos vídeos:

![](./img/13.png)

Nosotros vamos a ejecutar uno para comprobar que lo podemos ver. Para ello, vamos al navegador web y ponemos en la URL `mms://IP.DE.LA.MV:5119/MediaRoot/test.avi` y seleccionamos el reproductor de Windows Media:

![](./img/14.png)

Seleccionamos la configuración recomendada del reproductor si es la primera vez que lo usamos:

![](./img/15.png)

Y comprobamos que podemos ver el vídeo correctamente y en el programa nos muestra que estamos conectados al servicio:

![](./img/16.png)

---

### 4. Creación de carpeta virtual <a id="4"></a>

Ahora vamos a crear una carpeta para poner nuestros vídeos. Para ello, le damos clic derecho en `File resources` y seleccionamos la opción `New virtual folder...`:

![](./img/17.png)

Le ponemos nombre a la carpeta virtual y le ponemos una ruta real donde tengamos alojados nuestros vídeos. El resto lo dejamos por defecto:

![](./img/18.png)

Y comprobamos que se muestran nuestros vídeos:

![](./img/19.png)

> Es recomendable usar vídeos en formato AVI en caso de reproducir en Windows, ya que el reproductor de Windows Media no tiene los códecs para reproducir vídeos MP4 en protocolo MMS.

---

### 5. Comprobación <a id="5"></a>

Finalmente vamos a reproducir nuestros vídeos. Para ello, vamos al navegador y ponemos en la URL `mms:/IP.DE.LA.MV:5119/Folder/video.avi` y seleccionamos el reproductor `VLC`, ya que Windows Media no funciona muy bien con el protocolo MMS:

![](./img/20.png)

Y vemos que podemos ver el vídeo correctamente y se muestra que estamos conectados en Unreal Media Server:

Vídeo 1:

![](./img/21.png)

Vídeo 2:

![](./img/22.png)
