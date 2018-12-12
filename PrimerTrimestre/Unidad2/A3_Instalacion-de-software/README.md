
# Instalar aplicaciones y actualizar el sistema (Windows + OpenSUSE)

---

## 1. Windows7 usando el GUI

### 1.1. Instalar características del sistema operativo

Instalé 3 características en el SO Windows:

* Cliente Telnet
* Buscaminas
* Solitario

![Telnet](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/telnet.png)
![Solitario-Buscaminas](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/busc-sol.png)

Para comprobar que se instalaron correctamente utilicé el comando:
`telnet towel.bklinkenlights.nl`

![Star Wars](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/StarWars.png)

Comprobé el cliente telnet de la siguiente forma:

1. Abrí una terminal y ejecuté `telnet 172.20.1.2 80`
2. Escribí `olleh`

> Con este comando se conecta con leela 172.20.1.2

![Leela](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/olleh.png)

### 1.2. Vamos a instalar aplicaciones

Para empezar, descargué Wget para Windows de la página oficial.
Una forma de comprobarlo, es verificar que el MD5 del fichero es el mismo que el de la página oficial. Para ello utilicé el programa `HashCalc`.

![MD5](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/fichero-md5.png)

---

## 2. Windows usando los comandos

### 2.1. Instalar programas

Descargué el programa GIT desde la web oficial (http://git-scm.com/)
Abrí una consola cmd y entré en la carpeta en la que descargué el fichero.

### 2.2. Desinstalar programas

A continuación desinstalé `Gedit Text Editor (64 bit)` por comandos, usando la consola `wmic`.
* Abrí una consola PowerShell como Administrador y ejecuté `wmic`
* Localicé los programas MSI instalados con `product get name`
* Tras esto, lo desinstalé con el comando `product where name="Gedit Text Editor (64 bit)"` y lo comprobé.

![Desinstalar Gedit](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/wmic.png)

### 2.3. Gestor de paquetes

Utilicé la aplicación Ninite para crear un paquete de instalación que contiene:

* Firefox
* VLC
* Gimp
* 7-Zip
* Steam

![Selección de apps](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/apps-ninite.png)

Una vez hecho el paquete, lo instalé.

![Paquete Ninite](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/pack-ninite.png)

---

## 3. Windows - Actualización del sistema

Instalé un paquete de actualizaciones para Windows7 para que tardaran menos tiempo.
Tras esto, reinicié Windows Update y descargué el paquete `KB3102810x64`
Reinicié la máquina, cy comprobé que Windows Update esta desactivado.

![Windows Update](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/winupd-desact.png)

Consulté las actualizaciones pendientes y elegí 3 para actualizar.

---

## 4. GNU/Linux usando el GUI

### 4.1. Instalar paquetes

El gestor de paquetes es un programa para instalar/desinstalar software como un AppStore.

Inicié el gestor de paquetes e instalé los siguientes programas:
* geany
* git
* gkrellm
* gtk-recordmydesktop

![Instalar Yast](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/inst-yast.png)

Comprobé dos programas para ver si se instalaron bien:

**Geany**

![Geany](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/geany-os.png)

**Gtk-recordmydesktop**

![Gtk-recordmydesktop](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/gtk-os.png)

### 4.2. Desinstalar paquetes

Desinstalé `gtk-recordmydesktop` con el gestor de paquetes y lo comprobé.

![Gtk-recordmydesktop Desinstalado](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/desinst-yast.png)

---

## 5. GNU/Linux usando los comandos

### 5.1. Instalar software

Ahora por consola como superusuario, instalé `Aisleriot Solitaire` con el comando `zypper install aisleriot`

![Aisleriot Solitaire](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/zypper-inst.png)

Tras esto comprobé que se instaló correctamente el programa:
* `zypper search aisleriot`

![zypper search](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/zypper-search.png)

* Ejecuté el programa y comprobé su funcionamiento
* Busqué el programa en el sistema de ficheros con el comando `whereis aisleriot`

![whereis aisleriot](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/whereis-app.png)

### 5.2. Desinstalar software

Desinstalé el programa con `zypper remove aisleriot`

![remove apps](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/remove-apps.png)

Tras esto comprobé que se desinstaló correctamente con los siguientes pasos:
* `zypper se aisleriot`

![zypper se](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/zypper-se.png)

* Busqué el programa en el sistema de ficheros con el comando `whereis aisleriot`

![No whereis](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/no-whereis-apps.png)



### 5.3. Instalar programa Windows

Instalé el emulador Windows `wine`
Después, descargué `Johnny Simulator` en GNU/Linux y lo instalé usando `wine`.

![Wine Johnny](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/johnny.png)

### 5.4. Instalar programa desde rpm

Para empezar, comprobé que el programa `atom` no estaba disponible en los repositorios.

![Atom](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/atom-repos.png)

Busqué en la web de `atom.io` el instalador para openSUSE y descargué el fichero `.rpm`.

![Descarga rpm](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/atom-rpm.png)

Instalé el programa con el comando `rpm -i atom.x86_64.rpm`

![Instalar atom](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/inst-atom.png)

Por si acaso requiera alguna dependencia, la instalé manualmente con:
* `zypper search lsb*` para buscar todos los paquetes lsb algo
* `zypper install lsb` para instalar el paquete lsb

![Paquetes lsb](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/lsb-atom.png)

Para comprobar que se instaló el paquete utilice los comandos:
* `rpm -q atom`
* `atom`

![Comprobar Atom](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/comp-atom.png)

### 5.5. Instalación desde el código fuente

Consulté la lista `Games on GitHub` y dentro de la sección `Native` elegí el programa **Space Shooter**.

![Space Shooter](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/spaceshooter.png)

---

## 6. GNU/Linux actualización del sistema

Entré en la consola como superusuario y ejecuté:
* `zypper refresh` para actualizar el catálogo de productos software disponible.
* `zypper update` para actualizar todas las aplicaciones del sistema.

![Zypper Refresh/Update](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A3_Instalacion-de-software/images/zypper-r-u.png)
