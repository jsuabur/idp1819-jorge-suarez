
# CD-Live vs instalación

---

## 1. Live CD

Descargué la ISO Live del sistema operativo Knoppix.

![Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/knoppix.png)

Creé una máquina virtual sin disco duro llamada `Knoppix`.

![Sin Disco Duro Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/discoduro.png)

![Knoppix VirtualBox](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/virtualbox-knoppix.png)

Una vez hecho esto, inicié el SO en modo Live y en español.

![Inicio Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/iniciar-knoppix.png)

Una vez probado el sistema, abrí un terminal y puse los siguientes comandos:
* `date`
* `ip a`
* `sudo blkid`

![Comandos Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/comandos-knoppix.png)

Después de introducir los comandos anteriores, creé unos ficheros y pude comprobar que al reiniciar la máquina los archivos no se guardaron.

**Antes de reiniciar**

![Antes de reiniciar Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/antes-reinicio-k.png)

**Después de reiniciar**

![Despues de reiniciar Knoppix](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/despues-reinicio-k.png)

---

## 2. Windows7

Descargué la ISO de `Windows7 enterprise sp1 x64` y creé una MV con disco duro.

![Windows MV](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/windows-mv.png)

Tras esto, inicié una instalación por defecto de Windows.

![](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/windows-mv.png)

Para personalizarla, introduje lo siguiente:
* Nombre de usuario: `jorge`
* Nombre del equipo: `suarez`

![Personalizar Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/pers-win.png)

Al terminar la instalación ejecuté una terminal `PowerShell` y capturé los siguientes comandos:

* `date`
* `ipconfig`
* `hostname`

![Comandos Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/ip-win.png)

---

## 3. GNU/Linux OpenSUSE

Descargué la ISO `openSUSE-Leap-42.3-DVD-x86  64.iso` y creé una MV con disco duro de 8GB.

![OpenSUSE MV](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/opensuse.png)

![Instalación OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/inst-os.png)

Tras esto, realicé una instalación por defecto cambiando:
* Nombre de usuario: `jorge`
* Nombre del equipo/host: `suarez`
* Nombre dominio: `burgos`

Tras terminar la instalación del sistema operativo, ejecuté el programa `Yast`. Una vez dentro, fui a `Nombre de Host/DNS` que está dentro de `Ajustes de red`:		
* Escribí el nombre del host/máquina `suarez`
* Escribí el nombre del dominio `burgos`
* Deshabilité la opción `Modificar nombre...`
* Activé `Asignar nombre...`

![Host OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/host-os.png)

Para finalizar, abrí una terminar y capturé la salida de los siguientes comandos:
* `hostname -f`
* `date`
* `ip a`
* `sudo blkid`
* `sudo fdisk -l`

![Comandos OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/cons1-os.png)

![Comandos OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A1_CDLive-vs-Instalacion/images/cons2-os.png)
