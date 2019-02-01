
# Clonezilla Remote Samba

---

## 2. Preparativos

### 2.1. MV1: Windows7

* Añadir un segundo disco de `100MB`
* Asignarle la letra `E:`
* Formatearlo en NTFS
* Grabar en él lo siguiente:
  * Fichero de texto `file1-24`
  * Imagen `file2-24`
  * Canción `file3-24`

![Preparativos Windows7](./images/ficheros-e.png)

### 2.2. MV2: Windows 2008 Server

*  Añadir un segundo disco de `1GB`
* Asignarle la letra `E:`
* Formatearlo en NTFS

**Carpeta para compartir**

Crear una carpeta llamada `samba24`

> Lectura/escritura para el usuario jorge

![Samba24](./images/samba24.png)


**Recurso compartido:**

* Compartir la carpeta

> Lectura/escritura para el usuario jorge

* Uso compartido avanzado
* Poner `imagenes24` como nombre del recurso compartido

![Imagenes24](./images/imagenes24.png)


### 2.3. Comprobar el recurso de red

Para comprobar el recurso de red, acedemos al recurso compartido desde Windows7 y creamos un fichero de texto. Si no se pudiera mirar los permisos.

![Comprobar red](./images/funciona-23.png)

---

## 3. Clonación

**Realizar clonación**

* La hacemos tipo `device-image`

![Device-Image](./images/device-image.png)

* Elegimos `samba_server` como repositorio de almacenamiento utilizando clave/usuario del *Windows Server*.

![Samba Server](./images/samba-server.png)

* Configuramos la tarjeta de red en modo *DHCP*

![DHCP](./images/dhcp.png)

* Modo `Begginer`

![Begginer](./images/begginer.png)

* Para guardar las particiones, utilizar `saveparts`.

![Saveparts](./images/saveparts.png)

* Elegir grabar solo el disco 2

![Grabar disco 2](./images/disco2.png)

**Comprobar que hay fichero de imagen en el servidor**

Consultamos el directorio `E:\samba24\` del servidor, debe estar la imagen de clonación hecha con clonezilla.

![Clonacion Servidor](./images/imagen-clonacion.png)

---

## 4. Restauración

Ahora vamos a restaurar.

* Iniciamos MV Windows7

![Iniciar Windows7](./images/iniciar-4.png)

* Eliminamos los ficheros del Windows7 (`file1-24`, `file2-24` y `file3-24`)

![Eliminar ficheros](./images/borrar-4.png)

* Iniciar con Clonezilla

![Clonezilla](./images/clonezilla-4.png)

* Utilizamos `restoreparts`

![Restauramos](./images/restaurar-4.png)

* Elegimos la imagen que restaurar y luego en que disco restaurarlo.

![Elegir imagen](./images/restaurar-img-4.png)

![Elegir disco donde restaurar](./images/part-restau-4.png)

* Comprobamos que se ha restaurado correctamente.

![Restaurado completo](./images/restaurado-completo-4.png)
