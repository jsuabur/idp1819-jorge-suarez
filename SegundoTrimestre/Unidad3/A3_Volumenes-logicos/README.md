
#Volúmenes Lógicos: Debian + Windows

---

## 1. Instalar SO sobre LVM

### 1.1. Preparar MV

Creamos una MV Debian con:
* Disco de 8GB
* Red en `modo puente`
* Una vez llegado al particionado, parar y realizar de la siguiente forma manualmente.

### 1.2. Particionar

**Partición BOOT**


**Partición para LVM**


![Particiones](./images/particion-lvm.png)

![Particionado Listo]

### 1.3. Comprobación de la instalación LVM



---

## 2. Aumentar el tamaño del VL en caliente

Ahora, ampliaremos el espacio de `lv24datos` de 100MB a 400MB.

### 2.1. Ampliamos



### 2.2. Comprobamos



---

## 3. Modificar el espacio físico LVM

Antes que nada hacer una snapshot de la MV por si acaso.

### 3.1. Preparar la MV



### 3.2. Crear VG y VL



### 3.3. Escribir información



### 3.4. Añadir más tamaño



### 3.5. Quitar un disco físico del VG



### 3.6. Comprobamos



---

## 4. Discos dinámicos en Windows


### 4.1. Volumen distribuido
