
# Raid OpenSUSE y Windows

---

## 1. Instalar OpenSUSE en disco RAID0 software

## 1.1. Creación de la MV

Crear una máquina virtual con 3  discos vituales SATA:
* `(a) 200MB`
* `(b) 10GB`
* `(c) 10GB`

### 1.2. Particionado e instalación

Empezar el proceso de instalación
Elegir particionado experto y crear las siguientes particiones:

Dispositivo | Tamaño | Tipo | Formato | Montar
----------- | ------ | ---- | ------- | ------
/dev/sda1 | 150MB | Partición | ext3 | /boot
/dev/sda2 | 50MB | Partición | fat32 | /boot/efi
/dev/sdb1 | 10GB | Partición | RAID |
/dev/sdc1 | 10GB | Partición | RAID |

![Particiones de OpenSUSE](./images/particiones-opensuse.png)

Creamos el nuevo volumen RAID-0 con `sdb1` y `sdc1`

Dispositivo | Tamaño | Tipo | Formato | Montar
----------- | ------ | ---- | ------- | ------
/dev/md/raid0a24 | 20GB | Partición | btrfs | /

![Raid0 de OpenSUSE](./images/raid0-suse.png)

### 1.3. Comprobación

Tras realizar las particiones y el RAID-0, lo comprobamos con los siguientes comandos:
* `date`
* `hostname`
* `ip a`
* `ip route`
* `host www.nba.com`
* `fdisk -l`
* `df -hT`
* `cat /proc/mdstat`
* `lsblk -fm`

![Raid0 de OpenSUSE](./images/comp1-opensuse.png)

![Raid0 de OpenSUSE](./images/comp2-opensuse.png)

![Raid0 de OpenSUSE](./images/comp3-opensuse.png)

![Raid0 de OpenSUSE](./images/comp4-opensuse.png)

---

## 2. RAID-1 software

Para prevenir algún contratiempo, haremos una instantánea de la MV.

### 2.1. Preparar la MV

Ahora añadiremos 2 discos virtuales del mismo tamaño:
* `(d) 500MB`
* `(e) 500MB`

Para comprobar que son `/dev/sdd` y `/dev/sde` utilicé el comando `fdisk -l`.

![Comprobar discos OpenSUSE](./images/comp-discos-opensuse.png)

### 2.2. Crear RAID-1

Creamos un RAID-1 con los discos `(d)` y `(e)` llamado `/dev/md/raid1a24`.

![RAID1 OpenSUSE](./images/raid1-opensuse.png)

Lo creamos en formato `ext4`.

![Formateo en ext4 OpenSUSE](./images/formateo-raid1-opensuse.png)

### 2.3. Comprobar RAID-1

Tras crearlo utilizaremos varios comandos para comprobar que se ha creado correctamente:
* `cat /proc/mdstat`
* `lsblk -fm`
* `mdadm --detail /dev/md/raid1a24`

![Comprobación RAID1 OpenSUSE](./images/comp1-raid1-opensuse.png)

![Comprobación RAID1 OpenSUSE](./images/comp2-raid1-opensuse.png)

### 2.4. Escribir datos en el RAID-1

Tras comprobar que se creó correctamente, montamos el dispositivo en `raid1disco24` con el comando:
> `mount /dev/md/raid1a24 /mnt/raid1disco24`

![Montar RAID1 OpenSUSE](./images/montar-raid1-opensuse.png)



### 2.5. Configuración de RAID-1



### 2.6. Montaje automático



---

## 3. Quitar disco y probar



---

## 4. Discos dinámicos en Windows



### 4.1. Volumen Seccionado (RAID-0)



### 4.2. Volumen Reflejado (RAID-1)



### 4.3. Pregunta RAID-5
