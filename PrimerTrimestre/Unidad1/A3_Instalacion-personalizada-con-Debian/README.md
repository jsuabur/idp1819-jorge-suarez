# Instalación personalizada con Debian

---

## 1. Preparar la Máquina Virtual

Creé una MV tipo Debian con:
* 10GB de Disco.
* Tarjeta de red en modo puente.

![Nombre Debian](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/nombre-debian.png)

![Capacidad Debian](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/esp-debian.png)

![Red Debian](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/red-debian.png)

---

## 2. Knoppix

Tras crear la MV, descargué la ISO de Knoppix y el fichero md5.

Comprobé que la descarga de los ficheros se hizo de forma correcta de la siguiente forma:
1. Abrí una terminal.
2. Entré en la carpeta en donde estaban mis archivos (en mi caso *Descargas*).
3. Utilicé el siguiente comando: `md5sum -c KNOPPIX_V7.6.0EN.md5`.

![Md5sum Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/md5sum-knoppix.png)

Inicié la MV con CDLive de Knoppix y pulse el botón *F3* y escribí `knoppix lang=es` para que se me iniciara en español.

![Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/cd-knoppix.png)

Tras iniciarse con éxito la máquina virtual de Knoppix, entré en la terminal como root, y ejecuté `gparted`.

![Gparted](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/gparted.png)

Una vez dentro, creé una tabla de particiones tipo *MSDOS (MBR)*, cuando la hice, creé una partición extendida que ocupó todo el disco y apliqué los cambios.

![Particiones Gparted](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/part-gparted.png)

---

## 3. Instalando SO Debian

Descargué la ISO de Debian y el fichero md5.

Comprobé que la descarga de los ficheros se hizo de forma correcta de la siguiente forma:
* Abrí una terminal.
* Entré en la carpeta en donde estaban mis archivos (en mi caso *Descargas*).
* Utilicé el siguiente comando: `md5sum -c Md5SUMS.debian940`.

![Md5sum Debian](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/md5sum-debian.png)

Tras comprobarlo, configuré la Máquina Virtual Debian con el siguiente particionado:
* Partición lógica para la Swap de 1GB (Tipo Área Intercambio).
* Partición lógica para la Raíz del sitema (Montar /) de 7GB tipo ext4.
* Partición lógica para el Home (Montar /home) de 5r00MB tipo ext3.
* Partición lógica sin usar (No se monta) de 100MB de tipo ext2.
* Dejé el resto sin usar.

![Particionado de discos](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/part-discos.png)

---

## 4. Con el SO instalado

Ejecuté los siguientes comandos de comprobación:
* `date`
*	`hostname -a`
*	`hostname -d`
*	`uname -a`
*	`ip a`
*	`df -hT`
*	`fdisk –list`
*	`lsblk`
*	`blkid`

![Comprobaciones](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/comp1.png)

![Comprobaciones](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/comp2.png)

![Comprobaciones](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/comp3.png)

---

## 5. Acceso externo

Accedí desde la máquina real, a la MV de Debian.

![SSH Server](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/ssh.png)

![Comando Halt](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A3_Instalacion-personalizada-con-Debian/images/halt.png)
