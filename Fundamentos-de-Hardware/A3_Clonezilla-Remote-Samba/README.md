
# Clonezilla Remote Samba

---

## 2. Preparativos

### 2.1. MV1: Windows7



### 2.2. MV2: Windows 2008 Server



**Carpeta para compartir**



**Recurso compartido:**



### 2.3. Comprobar el recurso de red



---

## 3. Clonación



**Realizar clonación:**



**Comprobar que hay fichero de imagen en el servidor:**

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
