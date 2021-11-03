# IIS Servidor Web avanzado - Windows Server

## 1. Crear zona de búsqueda directa ***miEmpresa***

Para realizar esta práctica vamos a crear una zona de búsqueda directa (ZBD) con el nombre de nuestra empresa (en nuestro caso, ***repcan.com***). Para crear la ZBD, vamos a nuestra MV de Windows Server y vamos a `Administrador del servidor -> Herramientas - DNS` :

![1-1](./img/01.png)

Ahora vamos a `Server -> ZBD`, le damos clic derecho y seleccionamos `Zona nueva...` :

![1.2](./img/02.png)

Los pasos de la ZBD son los siguientes:

* **Tipo de zona:** Principal.

* **Ámbito de replicación de zona:** Para todos los servidores... en este **dominio**.

* **Nombre de la zona:** Nuestra empresa. En nuestro caso, ***repcan.com***.

* **Actualización dinámica:** Sólo actualizaciones seguras.

  ![1.3](./img/03.png)

  > ***IMPORTANTE:*** Todos los pasos serán por defecto como está mencionado, lo único que cambiamos es el nombre de la zona.

Con esto ya tendremos la ZBD creada:

![1.4](./img/04.png)

---

## 2. Crear sitio web ***www.miEmpresa.com***

Ahora vamos a crear la zona web de la ZBD creada anteriormente. Para empezar, creamos la carpeta `miEmpresa` en la ruta `C:\` y dentro de la carpeta crearemos la subcarpeta `principal`. También se pueden crear las carpetas desde **cmd** utilizando el comando `mkdir` :

![2.5](./img/05.png)

Vamos a crear el sitio web. Para ello, vamos a `Administrador del servidor -> Herramientas -> IIS` :

![2.6](./img/06.png)

Luego vamos a `Server -> Sitios`, le damos clic derecho y seleccionamos `Agregar sitio web...` :

![2.7](./img/07.png)

Al agregar el sitio, debería verse de la siguiente manera:

![2.8](./img/08.png)

Ahora volvemos a `Administrador del servidor -> Herramientas - DNS -> Server -> ZBD -> miEmpresa` y dentro le damos clic derecho y seleccionamos `Host nuevo (A o AAAA)...` :

![2.9](./img/09.png)

Ponemos el nombre y la dirección IP del equipo servidor:

![2.10](./img/10.png)

Ahora le damos de nuevo clic derecho y seleccionamos `Alias nuevo (CNAME)...` :

![2.11](./img/11.png)

Ponemos como nombre ***www*** y le asignamos el host que acabamos de agregar:

![2.12](./img/12.png)

El dominio debería verse así:

![2.13](./img/13.png)

Ahora vamos al explorador de archivos y creamos un fichero ***index.html*** en la ruta `C:\miEmpresa\principal` :

![2.14](./img/14.png)

Editamos el fichero, añadimos imágenes y estilos.

Cuando ya esté todo listo, abrimos un navegador y en el cuadro de búsqueda escribimos `www.miEmpresa.com` y nos debería cargar el fichero ***index.html*** creado y modificado anteriormente:

![2.15](./img/15.png)

---

## 3. Crear sitio web ***pagos.miEmpresa.com***

En este paso vamos a crear el sitio web ***pagos.miEmpresa.com***, utilizando certificado autofirmado para acceder de forma segura, es decir, mediante `https`.

### 3.1. Crear certificado para acceso HTTPS

Lo primero que haremos es crear la carpeta `pagos` dentro del directorio `C:\repcan` :

![3.16](./img/16.png)

Una vez creado el directorio del sitio web, procedemos a ir a **ISS** y en `Server` vamos a `Certificados de servidor` :

![3.17](./img/17.png)

Dentro, vamos al lado derecho (`Acciones`) y le damos clic a `Crear certificado autofirmado...` :

![3.18](./img/18.png)

Especificamos el nombre y lo almacenamos en el hospedaje de sitios web:

![3.19](./img/19.png)

Debería verse así después de crearse:

![3.20](./img/20.png)

Ahora vamos a `Server -> Sitios`, le damos clic derecho y le damos a `Agregar sitio web...`. Debe tener los siguientes parámetros:

![3.21](./img/21.png)

Ya creado debería aparecer en `Sitios` :

![3.22](./img/22.png)

Finalmente, para que nos funcione tanto de manera normal (http) como de manera segura (https), debemos ir a `Sitios -> pagos -> Acciones -> Enlaces...` y definir el sitio que falta:

![3.23](./img/23.png)


### 3.2. Crear subdominio

Ahora vamos a `Administrador del servidor -> Herramientas - DNS -> Server -> ZBD -> miEmpresa`, le damos clic derecho y seleccionamos `Dominio nuevo...` :

![3.24](./img/24.png)

Ponemos el nombre:

![3.25](./img/25.png)

Y finalmente le añadimos el host y el alias:

![3.26](./img/26.png)

### 3.3. Comprobación

Vamos al explorador de archivos y creamos un fichero ***index.html*** en la ruta `C:\miEmpresa\pagos` :

![3.27](./img/27.png)

Editamos el fichero, añadimos imágenes y estilos.

#### Desde el servidor

Cuando ya esté todo listo, abrimos un navegador y en el cuadro de búsqueda escribimos `www.pagos.miEmpresa.com` y nos debería cargar el fichero ***index.html*** creado y modificado anteriormente:

* De manera normal (http):

  ![3.28](./img/28.png)

* De manera segura (https):

  ![3.29](./img/29.png)

#### Desde el cliente

Desde el cliente haremos lo mismo, abrimos un navegador y en el cuadro de búsqueda escribimos `www.pagos.miEmpresa.com` y nos debería cargar el fichero ***index.html*** creado y modificado anteriormente:

* De manera normal (http):

  ![3.30](./img/30.png)

* De manera segura (https):

  ![3.31](./img/31.png)


---

## 4. Crear sitio web ***tienda.miEmpresa.com***

En este paso vamos a crear el sitio web ***tienda.miEmpresa.com***, utilizando certificado OpenSSL para acceder de forma segura.

### 4.1. Instalar OpenSSL

Lo primero es instalar el software e instalarlo. Una vez descargado, realizaremos los pasos de instalación:

* Introducción:

  ![4.32](./img/32.png)

* **Términos de licencia:** Leemos y aceptamos:

  ![4.33](./img/33.png)

* **Ruta de instalación:** La que queramos:

  ![4.34](./img/34.png)

* **Directorio de menú inicio:** Por defecto:

  ![4.35](./img/35.png)

* Instalación:

  ![4.36](./img/36.png)

Una vez realizados los pasos, ya tendremos instalado OpenSSL.

### 4.2. Generar certificado de servidor

Abrimos el comando y accedemos a la carpeta `C:\OpenSSL\bin` con el comando `cd`. Una vez en la ruta, ejecutamos el comando `openssl genrsa -des3 -out cakey.pem 2048` y creamos una clave. Esto creará una clave privada:

![4.37](./img/37.png)

Al abrir el contenido del fichero `cakey.pem` podemos ver la clave:

![4.38](./img/38.png)

Ahora vamos a crear el certificado digital de la CA que contendrá información sobre la misma. Para ello, ejecutamos el comando `openssl req -new -x509 -key cakey.pem -out cacert.pem -days 365`. Nos pedirá la clave del fichero `cakey.pem`, nacionalidad, provincia, ciudad, organización (empresa), puesto de organización, nombre y correo, por lo que lo rellenamos:

![4.39](./img/39.png)

Al abrir el contenido del fichero `cacert.pem` podemos ver el certificado:

![4.40](./img/40.png)

Creamos el fichero `certreq.txt` dentro de la ruta `C:\OpenSSL\bin` con el comando `copy con` :

![4.41](./img/41.png)

Vamos a ISS y en `Server` le damos a `Certificados de servidor` :

![4.42](./img/42.png)

Dentro le damos clic en `Acciones -> Crear una solicitud de certificado...` :

![4.43](./img/43.png)

Rellenamos los campos que se muestran a continuación:

![4.44](./img/44.png)

Pondremos el proveedor de servicios criptográficos por defecto y pondremos una longuitud de 4096 bits:

![4.45](./img/45.png)

Especificamos la ruta del fichero creado anteriormente:

![4.46](./img/46.png)

Y finalizamos. Ahora vamos a crear el certificado digital de nuestra web. Para ello, volvemos a cmd y ejecutamos el comando `openssl x509 -req -days 365 -in certreq.txt -CA cacert.pem -CAkey cakey.pem -CAcreateserial -out iis.crt` :

![4.47](./img/47.png)

Al abrir el contenido del fichero `iis.crt` podemos ver el certificado:

![4.48](./img/48.png)

### 4.3. Importar certificado

Vamos a `IIS -> Server -> Certificados de servidor -> Acciones` y seleccionamos `Completar solicitud de certificado...` :

![4.49](./img/49.png)

Especificamos el certificado `iis.crt`, le pondremos un nombre descriptivo y almacenamos en el hospedaje de sitios web:

![4.50](./img/50.png)

### 4.4. Requerir acceso seguro

Ahora creado el certificado y preparado, vamos a crear la estructura de carpetas. Para ello, crearemos la carpeta `tienda` en la ruta `C:\repcan\`, creamos también subcarpetas y el fichero ***index.html***. Creamos las carpetas con el comando `mkdir` y los ficheros con el comando `copy con` :

![4.51](./img/51.png)

Vamos a `IIS -> Server -> Sitios`, le damos clic derecho y le damos a crear sitio web. Pondremos los siguientes parámetros:

![4.52](./img/52.png)

Luego le damos a `Sitios -> tienda -> Acciones` y le damos clic a `Enlaces...`. Quitamos el enlace **http**, de tal manera que sólo esté el de **https**:

![4.53](./img/53.png)

Vamos a `DNS -> Server -> ZBD -> miEmpresa` y creamos el subdominio `tienda`. En él añadimos los hosts y alias correspondientes:

![4.54](./img/54.png)

Preparamos los ficheros para la visión del sitio web:

![4.55](./img/55.png)

Y ya podemos comprobar.


### 4.5. Comprobación

#### Desde el servidor

* De manera normal (http):

  ![4.56](./img/56.png)

* De manera segura (https):

  ![4.57](./img/57.png)

  ![4.58](./img/58.png)

#### Desde el cliente

* De manera normal (http):

  ![4.59](./img/59.png)

* De manera segura (https):

  ![4.60](./img/60.png)


> ***IMPORTANTE:*** Como podemos ver, al entrar de manera normal (http), no nos resuelve el sitio web y nos resuelve el sitio web del dominio principal, esto se debe gracias a que quitamos el enlace http al crear el sitio web.
---

## 5. Crear sitio web ***empleados.miEmpresa.com***

Finalmente vamos a crear el sitio ***empleados.miEmpresa.com*** utilizando validación de usuario para su respectiva carpeta o sitio.

Para empezar, accedemos a la ruta `C:\repcan` con el comando `cd` y creamos las carpetas `comun`, `david`, `alejandro` y `alexander`. Utilizaremos el comando `mkdir` y comprobamos con el comando `tree` :

![5](./img/61.png)

Vamos a `IIS -> Server -> Sitios`, le damos a `Nuevo sitio web...` y creamos el sitio `empleados` con los siguientes parámetros:

![5](./img/62.png)

Luego en el sitio `empleados`, le damos a `Acciones -> Editar permisos -> Opciones avanzadas`:

![5](./img/63.png)

Y le damos a `Deshabilitar herencia`. Borramos todas las herencias:

![5](./img/64.png)

Una vez hecho, vamos a `Administrador del servidor -> Herramientas -> Usuarios y equipos de AD`:

![5](./img/65.png)

Vamos a `Users`, le damos clic derecho y seleccionamos `Nuevo -> Grupo`:

![5](./img/66.png)

Creamos el grupo `empleados`:

![5](./img/67.png)

Seguimos en `Users`, le damos clic derecho y seleccionamos `Nuevo -> Usuario`:

![5](./img/68.png)

Y creamos los usuarios `david`, `alexander` y `alejandro`:

![5](./img/69.png)

Ponemos contraseña a cada usuario:

![5](./img/70.png)

Y el resultado debe verse así:

![5](./img/71.png)

Le damos clic derecho a los usuarios creados y le damos a `Agregar a un grupo`. Los agregamos al grupo `empleados`:

![5](./img/73.png)

Comprobamos el grupo `empleados` desde `Propiedades -> Miembros`:

![5](./img/72.png)

Ahora vamosa a `DNS -> Server -> ZBD` y creamos un dominio nuevo y le agregamos sus respectivos hosts y alias:

![5](./img/74.png)

Volvemos a `IIS -> Server -> Sitios -> empleados -> Autenticación`, deshabilitamos autenticación anónima y habilitamos autenticación básica:

![5](./img/76.png)

Ahora preparamos la estructura del sitio web y le damos clic derecho en las carpetas de los usuarios y le damos a `Propiedades`:

![5](./img/77.png)

Le damos a `Opciones avanzadas`:

![5](./img/78.png)

Cambiamos el propietario:

![5](./img/79.png)

Ponemos de propietario el grupo `empleados`:

![5](./img/80.png)

Ahora le damos a `Agregar`:

![5](./img/81.png)

Agregammos el `usuario` de la carpeta y le ponemos permisos de `Control total`:

![5](./img/82.png)

Debería verse así:

![5](./img/83.png)

Hay que hacer lo mismo con cada carpeta. En el caso de la carpeta común, poner de propietario el grupo y entidad de seguridad `empleados`.

Finalmente abrimos el navegador web y en el cuadro de búsqueda buscamos `www.empleados.miEmpresa.com` y nos saldrá un index de chequeo de empleados. Sólo se podrá acceder a la carpeta el usuario de la misma, por lo que pedirá usuario y contraseña (exepto la carpeta común, que todos tienen acceso a él):

![5](./img/84.png)

Al loguearse correctamente, se abrirá su sitio web.

* David:

  ![5](./img/85.png)

* Alejandro:

  ![5](./img/86.png)

* Alexander:

  ![5](./img/87.png)

* Común:

  ![5](./img/88.png)
