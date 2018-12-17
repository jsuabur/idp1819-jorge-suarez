
# Instalación dual

---

## 1. Preparar la máquina virtual

Creé una máquina virtual con la siguiente configuración:
* Tipo Windows 7 (64 bits).
* RAM 1024MB.
*	Disco duro de 18GB.
*	Tarjeta de red en modo puente.

![Configuración Windows7 VirtualBox](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/vb-windows.png)

### 1.1. Particionado

Inicié la MV con un CD-LIVE de Knoppix para hacer el particionado.

Abrí una terminal y ejecuté gparted para hacer las siguientes particiones:
- Una partición primaria, tipo *NTFS* para Windows (12GB).
- Una primaria *FAT32* para datos (100MB).
- Creé una partición extendida que cogiera el resto del disco.

Dentro de la extendida hice las siguientes particiones lógicas:
- Área de intercambio o *SWAP* (500MB).
- Partición de tamaño 100MB y con formato *ext3*.
- Partición de tamaño 5GB y con formato *ext4*.
- Dejé libre 300MB que no utilicé.

![Particion Gparted](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/particionado.png)

---

## 2. Instalación del primer SO

### 2.1. Configuración de la MV

Empecé instalando el SO Windows. Monté la ISO, con idioma español e instalación personalizada. Tras la instalación, configuré la Máquina Virtual de Windows de la siguiente forma:

![Ip Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/ipconfig.png)

Para comprobar la conexión utilicé el comando `ping www.google.es`.

![Ping Google](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/ping.png)

Después, fui a `Administración de discos` dentro de `Almacenamiento` para comprobar las particiones.

![Particion Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/part-windows.png)

Para finalizar, modifiqué la configuración de Windows Update y la deshabilité.
Configuré el grupo de trabajo con `curso1819` y el nombre del equipo como `suarez24w`.

![Nombre Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/nombre-windows.png)

### 2.2. Acceso remoto (Telnet)

Para empezar instalé el `Servidor Telnet`  y lo configuré de la siguiente forma:
* Inicié el servicio.
* Y apliqué que el tipo de inicio fuera automático.

![Telnet](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/telnet.png)

Creé un usuario llamado `sysadmingame` dentro de los grupos `Administradores` y `TelnetClients`.

La clave será `*******`

![Telnet Administradores](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/admin-windows.png)

![Telnet Clientes](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/telnet-windows.png)

Tras hacer esto, probé si el telnet funcionaba desde la máquina real, poniendo la dirección IP de la MV Windows: `telnet 172.18.24.11`.

![Comprobar Telnet](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/comp-windows.png)

---

## 3. Instalación del segundo SO

### 3.1. Empezamos con la ISO

Antes de empezar, hice una captura de la MV, por si acaso.

Puse la ISO de OpenSUSE y la inicié cambiando el idioma a `Español`.

### 3.2. Particionado

Elegí instalación nueva y desactivé la configuración automática.

Entré en modo experto y utilicé el siguiente esquema de particiones:
* Área de intercambio o *SWAP* (500 MB).
* Partición home (montar `/home`) de tamaño 100 MB y con formato *ext3*.
* Partición del sistema (montar `/`) de tamaño 5 GB y con formato *ext4*
* Quedó un espacio libre.

![Particionado OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/formato-os.png)

### 3.3. Entorno, usuario y SSH

Elegí la zona horaria de Canarias y después, seleccioné el entorno gráfico `XFCE`.

### 3.4. Instalar

Instalé la MV y la configuré de la siguiente forma:
* IP estática: `172.18.24.31`
*	Nombre del host/equipo: `suarez24g`

![Ip Fija OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/ipfija-os.png)

![Host/Dominio OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/hostdominio-os.png)

Comprobé que la conexión de red haciendo ping a google: `ping www.google.es`.

![Ping Google OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/ping-os.png)

### 3.5. Con el SO instalado

Entré en el usuario root y ejecuté los siguientes comandos de comprobación:
* `date`
* `hostname`
* `uname -a`
* `ip a`
* `df -hT`
* `fdisk -l`
* `lsblk`

![Comprobación OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/comp1-os.png)

![Comprobación OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/comp2-os.png)

---

## 4. Menú de arranque

### 4.1. Cambiar el menú de arranquede Windows

Inicié el GNU/Linux y desde el usuario root creé un archivo nuevo para el arranque de Windows dentro de la carpeta */etc/grub.d* con el siguiente contenido:

>	#!/bin/sh -e
>
>	echo "Adding Windows 7" >&2
>
>	cat<<EOF
>
>	menuentry "Windows 7 (nombre-del-alumno - curso1819)" {
>
>	set root=(hd0,1)
>
>	chainloader +1
>
>	}
>
>	EOF

![Menú de arranque Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A5_Instalacion-dual/images/arranque-windows.png)
