
# Volúmenes Lógicos: Debian + Windows

---

## 1. Instalar SO sobre LVM

### 1.1. Preparar MV

Creamos una MV Debian con:
* Disco de 8GB
* Red en `modo puente`
* Una vez llegado al particionado, parar y realizar de la siguiente forma manualmente.

### 1.2. Particionar

**Partición BOOT**

Partición | Tamaño | Formato | Montaje
--------- | ------ | ------- | -------
Primaria | 100MB | ext2 | /boot

**Partición para LVM**

Crearemos una partición lógica, de tipo `LVM` con todo lo que nos queda de espacio en disco.
Crearemos un Grupo de Volumen llamado `vg24debian`.

Volumen Lógico | Tamaño | Formato | Montaje
--------- | ------ | ------- | -------
lv24swap | 500MB | swap | intercambio
lv24raiz | 5GB | ext4 | /
lv24datos | 100MB | ext3 | /home

![Particiones](./images/particion-lvm.png)

![Particionado Listo](./images/particion-listo-lvm.png)

Tras particionar, terminamos la instalación y la configuración del sistema operativo.

### 1.3. Comprobación de la instalación LVM

Reiniciamos el sistema y comprobamos que lo tenemos bien con los siguientes comandos:
* `date`
* `hostname -f`
* `ip a`

![Comprobacion dhi](./images/comprobacion-13-1.png)

* `fdisk -l`

![Comprobacion fdisk](./images/comprobacion-13-2.png)

* `vgdisplay`

![Comprobacion vgdisplay](./images/comprobacion-13-3.png)

* `lvdisplay vg24debian`

![Comprobacion swap](./images/comprobacion-13-swap.png)

![Comprobacion raiz y datos](./images/comprobacion13-raiz-datos.png)

---

## 2. Aumentar el tamaño del VL en caliente

Ahora, ampliaremos el espacio de `lv24datos` de 100MB a 400MB.

### 2.1. Ampliamos

Para empezar consultamos el tamaño actual del volumen lógico con:
`lvdisplay -v /dev/vg24debian/lv24datos`

![Consultar lv24datos](./images/consultar-datos.png)

Luego ampliamos el tamaño del volumen lógico con:
`lvextend --resizefs -L 400 /dev/vg24debian/lv24datos`

![Extender lv24datos](./images/extender-datos.png)

Después, consultamos el tamaño actual con el primer comando.

![Consultar actual lv24datos](./images/consultar-actual-datos.png)

### 2.2. Comprobamos

Ahora, comprobamos que hemos aumentado correctamente el tamaño de `lv24datos` con los siguientes comandos:
* vgdisplay

![Comprobar bgdisplay 2.2](./images/vgdisplay-22.png)

* lvdisplay vg24debian

![lvdisplay 2.2](./images/lvdisplay-swap-22.png)

![lvdisplay 2.2](./images/lvdisplay-raiz-datos-22.png)

* df -hT

![Comprobar tamaño](./images/dfhT-22.png)

---

## 3. Modificar el espacio físico LVM

Antes que nada hacer una snapshot de la MV por si acaso.

### 3.1. Preparar la MV

Añadimos dos discos virtuales:
  * Disco *B* de `200MB`: con una partición completa del disco.
  * Disco *C* de `750MB`: con 3 particiones de 250MB sin formato, ni tipo.

Yo creé las particiones con el programa `gparted`.

![Gparted Discos](./images/.png)

### 3.2. Crear VG y VL



### 3.3. Escribir información



### 3.4. Añadir más tamaño



### 3.5. Quitar un disco físico del VG



### 3.6. Comprobamos
