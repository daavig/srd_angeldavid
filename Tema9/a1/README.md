# Instalación y configuración de un Servidor de VoIP sobre Windows 2016

---

## Trabajo realizado por Ayoze Hernández y Ángel David González Quintana

---

## Índice


* [1. Registro e instalación de 3CX Phone System](#1)

* [2. Configuración del servidor](#2)

* [3. Instalación de 3CX Phone en el cliente y servidor](#3)

* [4. Creación de usuarios](#4)

* [5. Vinculaciones](#5)

* [ANEXO. Errores o problemas](#6)

---

### 1. Registro e instalación de 3CX Phone System <a id="1"></a>

Antes de empezar con esta práctica, vamos a necesitar las siguientes MVs:

* Servidor 3CX Phone System -> Windows Server 2016

* Cliente 3CX Phone -> Windows 7

* Cliente 3CX -> Dispositivo móvil

Para empezar con esta práctica, abriremos la MV de Windows Server y nos registramos en [3CX](https://www.3cx.es):

![](./img/01.png)

Luego nos logueamos y tendremos que completar la cuenta. Para ello, rellenamos los siguientes datos:

* **Tipo de cuenta:** Personal

* **País/Provincia:** Nuestra localización.

* **Información de contacto:** Nuestros datos.

* **Contraseña:** Ponemos la que queramos.

  ![](./img/02.png)

Una vez completa la información necesaria para nuestra cuenta, vamos a descargar el instalador. Para ello, vamos a `Mi Suscripción -> First Configuration -> On- Premise`:

![](./img/03.png)

Cambiamos el nombre de dominio sugerido:

![](./img/04.png)

Y seleccionamos la instalación para Windows:

![](./img/05.png)

Una vez descargado el instalador, lo ejecutamos y procedemos con los pasos de instalación:

* **Requisitos:** Solo nos dirá que requisitos necesitamos para instalar 3CX Phone System, por lo que seguimos:

  ![](./img/06.png)

* **Recomendaciones:** Solo nos recomendará algunas acciones, por lo que seguimos:

  ![](./img/07.png)

* **Términos de licencia:** Leemos y aceptamos:

  ![](./img/08.png)

* **Directorio de instalación:** Seleccionamos la ruta de instalación que queramos, aunque lo podemos dejar por defecto:

  ![](./img/09.png)

Una vez realizados los pasos, el servicio se instalará:

![](./img/10.png)

---

### 2. Configuración del servidor <a id="2"></a>

Una vez instalado, se abrirá la siguiente interfaz de texto con dos opciones de realizar la configuración, seleccionamos la opción de configuración a través del navegador web:

![](./img/16.png)

Se abrirá una página con la instalación y configuración del servidor, por lo que seguiremos los siguientes pasos:

* **Tipo de instalación:** Crear una nueva instalación del Sistema Telefónico 3CX (Ponemos la clave de licencia en nuestro perfil `My subscription` en 3CX):

  ![](./img/17.png)

* **Credenciales de la consola de administración 3CX:** Ponemos usuario y contraseña:

  ![](./img/18.png)

* **Dirección IP Pública:** Seleccionamos la primera opción:

  ![](./img/19.png)

* **Tipo de IP Pública:** Estática:

  ![](./img/20.png)

* **Selección de puertos:** Lo dejamos por defecto:

  ![](./img/21.png)

* **Adaptador de red:** Seleccionamos el único que tenemos.

* **FQDN:** Pondremos nuestro FQDN o dominio.

  ![](./img/22.png)

  ![](./img/23.png)

* **Longuitud de las extensiones:** 3 Dígitos:

  ![](./img/24.png)

* **Email del administrador:** Ponemos nuestro correo:

  ![](./img/25.png)

* **País y Zona Horaria:** Ponemos nuestros datos:

  ![](./img/26.png)

* **Extensión del operador:** Creamos un usuario operador:

  ![](./img/27.png)

* **Países a los que puede llamar:** Europa:

  ![](./img/28.png)

* **Idioma:** Spanish Prompts Set:

  ![](./img/29.png)

* **Información de Registro:** Ponemos nuestros datos (El ID de Partner es opcional)

  ![](./img/30.png)

Finalmente ya tendríamos 3CX instalado y configurado:

![](./img/32.png)

---

### 3. Instalación de 3CX Phone en el cliente y servidor <a id="3"></a>

Ahora tanto en el servidor como en el cliente Windows, realizaremos la siguiente instalación.

Vamos a la página de [3CX Softphone](https://www.3cx.es/voip-telefono/softphone/) y descargamos el instalador:

![](./img/11.png)

Una vez descargado, lo ejecutamos y seguiremos los siguientes pasos de instalación:

* **Bienvenida:** Nos dará la bienvenida. Seguimos:

  ![](./img/12.png)

* **Términos de licencia:** Las leemos y aceptamos:

  ![](./img/13.png)

* **Directorio de instalación:** Seleccionamos la ruta de instalación:

  ![](./img/14.png)

Finalmente se instalará y se abrirá la siguiente interfaz. Lo dejamos como está:

![](./img/15.png)

---

### 4. Creación de usuarios <a id="4"></a>

Ahora accedemos al enlace que nos sale al finalizar la configuración del servidor 3CX Phone System y nos logueamos:

![](./img/33.png)

Nos saldrá un código QR de instalación de 3CX para dispositivos móviles:

![](./img/34.png)

Crearemos 3 usuarios con los datos que queramos:

![](./img/35.png)

Y debería quedar así:

![](./img/36.png)

---

### 5. Vinculaciones <a id="5"></a>

Primero vinculamos el teléfono del servidor, para ello, le damos a `Auto Provision` y en `Teléfonos` nos saldrá el intento de acceso, lo seleccionamos y le damos a `Asignar Ext`:

![](./img/37.png)

Seleccionamos el usuario:

![](./img/38.png)

Le damos en `Aceptar`:

![](./img/39.png)

Y el teléfono del servidor ya estaría vinculado al usuario operador:

![](./img/40.png)

Comprobamos que el usuario vinculado está operativo:

![](./img/41.png)

Ahora vinculamos el teléfono cliente, para ello, le damos `Auto Provision` y en `Teléfonos` nos saldrá el intento de acceso, lo seleccionamos y le damos a `Asignar Ext`:

![](./img/42.png)

Seleccionamos el usuario:

![](./img/43.png)

Aceptamos y el teléfono del cliente ya estaría vinculado al usuario. Comprobamos que el usuario vinculado está operativo:

![](./img/44.png)

Finalmente podemos marcar la extensión de un teléfono a otro y podemos llamar correctamente.

---

### ANEXO. Errores o problemas <a id="6"></a>

No he podido realizar capturas de las llamadas debido a que el servidor no me permite acceder a la página web de administración, supongo a que tenía la dirección IP dinámica y este perdió la señal. Pero pude realizar las llamadas cuando hice la práctica y funcionaban.

Intenté acceder al usuario **Salva** desde mi teléfono móvil pero el código QR no funcionaba y manualmente tampoco.
