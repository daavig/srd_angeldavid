<center>

# Instalación de servidor VoIP en Linux: FreePBX

</center>

---

Trabajo realizado por: Ángel David González y Ayoze Hernández.

Curso: Administración de Sistemas Informáticos en Redes.

---

### ÍNDICE

+ [Instalación](#id1)
+ [Configuración](#id2)
+ [Creación de usuarios](#id3)
+ [Conexión entre dispositivos](#id4)



#### ***Instalación***. <a name="id1"></a>

Empezamos instalando la ISO de [FreePBX](https://www.freepbx.org/) e instalandola.

![](./img/001.png)

![](./img/002.png)

Debemos establecer una contraseña para el root. (Por motivos de seguridad no se muestra).

![](./img/004.png)

Una vez añadimos la contraseña se instalan los componentes necesarios.

![](./img/005.png)

#### ***Configuración***. <a name="id2"></a>

Accedemos a la página de configuración web de FreePBX mediante la IP de la máquina en cuestión.

![](./img/006.png)

Ahora procedemos a configurar el servidor con opciones por defecto.

![](./img/007.png)

Aquí debemos añadir nuestros datos de contacto (Pueden ser inventados).

![](./img/008.png)

Activamos el servidor con el comando: fwconsole sysadmin activate **clave**; la clave se nos proporciona al hacer click en "Activate".

![](./img/009.png)

Ya el resto de opciones que viene son por defecto por lo que no hay mucho que explicar de ellas.

![](./img/011.png)

![](./img/012.png)

![](./img/013.png)

![](./img/014.png)

![](./img/015.png)

![](./img/016.png)

![](./img/017.png)

#### ***Creación de usuarios***. <a name="id3"></a>

Para añadir un usuario debemos ir a **Applications>Extensions>Add-Extension**.

![](./img/018.png)

En la sección general añadimos los datos personales del usuario además de la contraseña e identificadores. Además podemos elegir entre 2 idiomas para el usuario.

![](./img/021.png)

En la sección avanzada debemos de cambiar la sección DTMF Signaling a automática.

![](./img/020.png)

Añadimos otro usuario de la misma manera.

![](./img/022.png)

#### ***Conexión entre dispositivos***. <a name="id4"></a>

Instalamos la aplicación de móvil e intentamos conectarnos con el servidor VoIP y vemos que nos reconoce el servicio SIP UDP.

![](./img/conexion1.jpeg)

Conectamos una cuenta.

![](./img/conexion2.jpeg)

Llamamos a la otra cuenta.

![](./img/conexion3.jpeg)

Comprobamos que recibe la llamada desde otro dispositivo y que suena a continuación.

![](./img/conexion4.jpeg)

![](./img/conexion5.jpeg)

Vemos que con exito se ha realizado la llamada.

![](./img/conexion6.jpeg)
