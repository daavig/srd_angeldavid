# Instalación y Configuración de Servicios de Correo Electrónico en Windows 2016 Server


En esta práctica aprenderemos a instalar y configurar un servidor SMTP en un sistema operativo Windows Server.

---

## Índice:

* [1. Servicio SMTP](#1)

  * [1.1. Instalar servicio SMTP](#1.1)

  * [1.2. Configuración del servicio SMTP (anónima)](#1.2)

  * [1.3. Comprobación desde el cliente](#1.3)

  * [1.4. Configuración del servicio SMTP (autenticación básica)](#1.4)

  * [1.5. Comprobación desde el cliente](#1.5)

* [2. hMailServer](#2)

  * [2.1. Desinstalar servicio SMTP](#2.1)

  * [2.2. Descargar e instalar hMailServer](#2.2)

  * [2.3. Configuración](#2.3)

  * [2.4. Comprobación desde el cliente](#2.4)

---

## 1. Servicio SMTP <a id="1"></a>

### 1.1. Instalar servicio SMTP <a id="1.1"></a>

Para empezar con esta práctica, vamos al `Administrador del Servidor -> Administrar -> Agregar roles y características`:

![](./img/01.png)

Seleccionamos la `Instalación basada en características o roles`:

![](./img/02.png)

Seleccionamos nuestro servidor:

![](./img/03.png)

Saltamos los roles y seleccionamos la característica `Servidor SMTP`:

![](./img/04.png)

Confirmamos e instalamos:

![](./img/05.png)

Finalmente esperamos a que finalize la instalación:

![](./img/06.png)

Con esto ya tendremos el servidor SMTP instalado, ahora falta configurarlo...

### 1.2. Configuración del servicio SMTP (anónima) <a id="1.2"></a>

Ahora vamos a configurar el servicio SMTP. Para ello, vamos a `Administrador del Servidor -> Herramientas -> IIS 6.0`:

![](./img/07.png)

Vamos a `Servidor -> SMTP Virtual...`, le damos clic derecho y seleccionamos `Propiedades`:

![](./img/08.png)

En `General`, configuraremos lo siguiente:

* **Dirección IP**: Todas las no asignadas

* **Limitar numero de conexiones a**: 50

* **Formato de registro activo**: Propiedades

![](./img/09.png)

* **Formato de registro activo -> Propiedades**: Programación diaria en el directorio `C:\Windows\System32\LogFiles`

![](./img/10.png)

En `Acceso` vamos a `Control de acceso -> Autenticación`:

![](./img/11.png)

Seleccionamos el acceso anónimo:

![](./img/12.png)

En `Acceso` vamos a `Control de conexión -> Conexión` y denegamos la conexión a un equipo con una IP determinada:

![](./img/13.png)

Luego le echamos un vistazo al resto de opciones:

**Mensajes**:

![](./img/14.png)

**Entrega**:

![](./img/15.png)

Comprobamos que tenemos un dominio AD determinado creado en el servicio SMTP:

![](./img/16.png)

Lo que haremos es crear un alias en el dominio anterior para disponer de cuentas de otro dominio:

![](./img/17.png)

Comprobamos que se ha creado correctamente:

![](./img/18.png)

Y finalmente comprobamos que se han creado las carpetas de correos en `C:\inetpub\mailroot`:

![](./img/19.png)

### 1.3. Comprobación desde el cliente <a id="1.3"></a>

Ahora vamos a nuestra máquina cliente y comprobamos que tenemos acceso al dominio abriendo una terminal y escribiendo el comando `nslookup accounts.tu.dominio`:

![](./img/20.png)

Podemos ver que tenemos acceso.

Ahora abrimos el navegador y vamos a la página oficial de [Pegasus Mail](http://www.pmail.com/downloads_s3_t.htm) y descargamos el instalador mediante el [siguiente enlace](http://download-us.pmail.com/w32-473.exe):

![](./img/21.png)

Una vez descargado vamos a instalarlo mediante los siguientes pasos:

* **Bienvenida**: Explica los que vas a descargar.

  ![](./img/22.png)

* **Detalles de instalación**: Ponemos la ruta en `C:\PMAIL`.

  ![](./img/23.png)

* **Otras opciones de instalación**: Seleccionamos todo.

  ![](./img/24.png)

Una vez realizados los pasos, se instalará:

![](./img/25.png)

Ejecutamos el programa y vamos a `Tools -> Internet Options`:

![](./img/26.png)

En `General`, ponemos nuestro correo electrónico:

![](./img/27.png)

En SMTP agregaremos un servidor de envío:

![](./img/28.png)

Ponemos nuestra dirección IP:

![](./img/29.png)

Y ya lo tendremos añadido:

![](./img/30.png)

![](./img/31.png)

Ahora enviaremos un correo de prueba:

![](./img/32.png)

Para enviar el correo, le damos al icono del planeta con la flecha para arriba:

![](./img/33.png)

En mi caso, este proceso me ha dado error.

![](./img/34.png)

### 1.4. Configuración del servicio SMTP (autenticación básica) <a id="1.4"></a>

En este apartado no se ha podido avanzar.

### 1.5. Comprobación desde el cliente <a id="1.5"></a>

En este apartado no se ha podido avanzar.

---

## 2. hMailServer <a id="2"></a>

### 2.1. Desinstalar servicio SMTP <a id="2.1"></a>

Para utilizar hMailServer, necesitamos desinstalar el servicio SMTP. Para ello, vamos a `Administrador del Servidor -> Administrar -> Quitar roles y funciones`:

![](./img/40.png)

Seleccionamos nuestro servidor:

![](./img/41.png)

Seleccionamos la característica `Servidor SMTP`:

![](./img/42.png)

Comprobamos que ya no está marcado:

![](./img/43.png)

Finalizamos y eliminamos la característica:

![](./img/44.png)

### 2.2. Descargar e instalar hMailServer <a id="2.2"></a>

Ahora vamos a descargar hMailServer. Para ello, vamos a la página oficial de [hMailServer](https://www.hmailserver.com/download) y descargamos el instalador mediante [este enlace](https://www.hmailserver.com/download_getfile/?performdownload=1&downloadid=262):

![](./img/45.png)

Una vez descargado lo instalamos. Para ello, seguiremos los siguientes pasos:

* **Bienvenida**: Te explica lo que vas a instalar. Seguimos.

  ![](./img/46.png)

* **Licencia**: La leemos y aceptamos.

  ![](./img/47.png)

* **Destino**: Ponemos la ruta por defecto.

  ![](./img/48.png)

* **Componentes**: Seleccionamos todo.

  ![](./img/49.png)

* **Seleccion de tipo de base de datos**: Built-in

  ![](./img/50.png)

* **Carpeta del menú inicio**: Lo dejamos por defecto.

  ![](./img/51.png)

* **Seguridad de hMailServer**: Necesitamos poner una contraseña para el uso como administrador.

  ![](./img/52.png)

Una vez realizados los pasos, instalamos:

![](./img/53.png)

Nos saldrá esta advertencia de que el programa requiere de `.NET Framework 2.0` y nos preguntará si queremos instalarlo, como estamos en el servidor debemos instalarlo de otra manera:

![](./img/54.png)

Ya que al darle a instalarlo nos saldrá un error:

![](./img/55.png)

Para instalar `.NET Framework 2.0` vamos a `Administrador del Servidor -> Administrar -> Agregar roles y características`:

![](./img/56.png)

Seleccionamos la característica `Características de .NET Framework 3.5 -> .NET Framework 3.5 (incluye .NET 2.0 y 3.0)`:

![](./img/57.png)

Instalamos y volvemos a la instalación de hMailServer. Realizamos los mismos pasos anteriores y ya se debería instalar correctamente:

![](./img/58.png)

### 2.3. Configuración <a id="2.3"></a>

Ahora vamos a ejecutar el programa. Nos dará un equipo al que conectarse y que pongamos una contraseña:

![](./img/59.png)

Una vez dentro creamos los dominios `asir.edu` y `srd.edu`:

![](./img/60.png)

Deberían quedar así:

![](./img/61.png)

Vamos a `Utilities -> Backup` y ponemos una ruta para guardar las backups:

![](./img/62.png)

Comprobamos en la ruta que se guardan las backups:

![](./img/63.png)

Vamos a `Utilities -> Diagnostics`, seleccionamos los domimios con el servidor mail del DNS al que hace el diagnóstico y le damos a `Start`. Luego lo guardamos en `Save`:

![](./img/64.png)

Vamos a `DNS` y creamos los dominios `asir.edu` y `srd.edu` con el servidor local y el intercambiador de correo:

![](./img/65.png)

![](./img/66.png)

Ahora crearemos dos usuarios en cada dominio, para ello, vamos a `Dominio -> Accounts` y los creamos dando clic en `Add`:

![](./img/67.png)

Ponemos nombre y contraseña:

![](./img/68.png)

Y hacemos lo mismo con los demás. Deberían quedar así:

![](./img/69.png)

![](./img/70.png)

Vamos ahora a `Settings -> Protocols -> SMTP` y ponemos nuestro servidor local:

![](./img/71.png)

Luego vamos a `Utilities -> MX-query` y ponemos la dirección e-mail y nos debe resolver la IP de nuestro servidor:

![](./img/72.png)

En `Settings -> Loggin` marcamos las siguientes casillas:

![](./img/73.png)

En `Settings -> Advanced -> IP Ranges` le damos clic en `Add`:

![](./img/74.png)

Le ponemos el nombre y el rango de IP:

![](./img/75.png)

Con esto ya tenemos configurado hMailServer.

### 2.4. Comprobación desde el cliente <a id="2.4"></a>

Instalamos ***Mozilla Thunderbird*** y agregamos un usuario local. Ponemos, usuario, correo y contraseña y pondremos la siguiente configuración manual:

![](./img/76.png)

Nos advertirá de que el servidor no usa encriptación, pero es nuestro servidor, por lo que aceptamos los riesgos:

![](./img/77.png)

Probamos a realizar un mensaje de correo al otro usuario del dominio hMailServer:

![](./img/78.png)

Agregamos el segundo usuario:

![](./img/79.png)

Comprobamos que hemos recibido el correo que hicimos con el usuario "david":

![](./img/80.png)

Y escribiremos otro correo para comprobar lo mismo:

![](./img/81.png)

Entramos con el usuario "david" y comprobamos que hemos recibido el correo del usuario "angel"

![](./img/82.png)

Ahora creamos una `Lista de distribución` con el nombre `empleados`:

![](./img/83.png)

Y hacemos miembros a los usuarios anteriores:

![](./img/84.png)

De aquí en adelante no he podido avanzar...
