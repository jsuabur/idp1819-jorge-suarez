
# Boot Loader

---

## 1. OpenSUSE

### 1.1. Añadir entrada SO Linux a GRUB2

Inicié la MV con GNU/Linux, tras esto entre en una terminal como superusuario.

Después, edité el fichero */etc/grub.d/40_custom* desactivando la línea:
`exec tail -n +3 $0`

Y añadiendo las siguientes líneas:
>	echo “[INFO] Estoy añadiendo entrada GNU/Linux” >&2
>
>	cat<<EOF
>
>	menuentry “Iniciar GNU/Linux (Jorge Suarez)” {
>
>	linux /boot/vmlinuz root=/dev/sda7
>
>	initrd /boot/initrd
>
>	}
>
>	EOF

![40_custom OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/40custom-os.png)

Guardé el fichero 40_custom y le di permisos de ejecución, tras esto hice una copia de seguridad del fichero de configuración y lo llamé *grub.000*. Actualicé los cambios y reinicié el sistema.

![40_custom Copia de Seguridad OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/40custom-cs-os.png)

Comprobé los cambios.

![Boot Loader OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/loader-os.png)

Inicié Yast2 desde comando y edite las Opciones del cargador de arranque.

![Yast2 Loader OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/yast2.png)

### 1.2. Añadir entrada SO Windows a GRUB2

Creé una nueva entrada del menú de carga para el SO Windows, añadiendo al fichero */etc/grub.d/40_custom* lo siguiente:
>	echo “[INFO] Añadiendo entrada Windows” >&2
>
>	cat<<EOF
>
>	menuentry “Iniciar Windows (Jorge Suarez)” {
>
>	set root=(hd0,1)
>
>	chainloader +1
>
>	}
>
>	EOF

![40custom Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/40custom-windows.png)

Comprobé que estaba bien configurado reiniciando la máquina.

### 1.3. Cambiar la apariencia

Abrí una terminal y cambié el color de la entrada de menú en rojo y de las entradas de menú seleccionada la dejé en negro.
Para personalizarlo aún más, puse de fondo algo relacionado con baloncesto.

Para ello, tuve que modificarlo en el fichero:

*/boot/grub2/themes/openSUSE/theme.txt*.

![Apariencia Loader](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/apariencia.png)

---

## 2. Windows7

### 2.1. Consultar la información

Consulté la información con el comando `bcdedit`.

![Windows Bcdedit](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/bcdedit.png)

### 2.2. Crear una nueva entrada

Creé una nueva entrada con los siguientes comandos:

`bcdedit /copy {current} /d “Jorge Suarez (2018)”`

`bcdedit /displayorder {49916baf-0e08-11db-9af4-000bdbd316a0} /addlast`

![Entrada Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad1/A7_Boot-Loader/images/entrada-bcdedit.png)
