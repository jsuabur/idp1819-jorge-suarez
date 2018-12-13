
# Claves y ocultación

---

## 1. SO Windows

### 1.1. Ocultación de usuarios

Modifiqué la configuración del sistema para que los usuarios `jedi1` y `jedi2`, no aparezcan en la ventana de inicio del sistema, de la siguiente forma:
* Inicié sesión con una cuenta de administrador.
* Ejecuté registry con el comando `regedit`.
* Exporte una copia de seguridad antes de cambiar la configuración.

![Ejecutar Registry](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/regedit.png)

Tras ejecutarlo entre en la carpeta  `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\` e hice lo siguiente:
* Cree una llave *(carpeta)* con el nombre: `SpecialAccounts`
* Dentro otra llave llamada: `UserList`
* Y en esta última creé dos registros de tipo `DWORD` con los nombres de las cuentas que quería ocultar:
  * `jedi1`
  * `jedi2`

![UserList](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/UserList.png)

Para acabar con la parte de ocultación de Windows, reinicie la MV y comprobé satisfactoriamente que se ocultaron los usuarios `jedi1` y `jedi2`.

![Jedis Ocultos](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/jedis-ocult.png)

### 1.2. Modo de incio de sesión seguro

Con este inicio se ocultan los nombres de todos los usuarios. Para hacerlo, seguí los siguientes pasos:
* Inicié una consola CMD como administrador.
* Ejecuté `secpol.msc`

![Comando secpol.msc](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/secpol.png)

* Fui a `Directivas locales > Seguridad` y habilité el `Inicio de sesión interactivo: No mostrar el último nombre`

![No mostrar el ultimo nombre](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/no-mostrar.png)

* En este tipo de inicio de sesión, debemos escribir nombre de usuario y su clave para iniciar sesión como he podido comprobar.

![Comprobar Usuario/Clave](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/comp-no-mostrar.png)

### 1.3. Claves seguras

Modifiqué las claves de los usuarios de la siguiente forma:
* `sith1`: 1234
* `sith2`: casa
* `jedi1`: frodoHOBBITbolson
* `jedi2`: gandalfELGRIS
* `jorge`: ******
* `administrador`: DNI

Tras esto, descargué la iso OphCrack para Windows7.

![iso OphCrack](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4A4_Claves-y-ocultacion/images/ophcrack.png)



---

## SO GNU/Linux

### 2.1. Ocultar usuarios

Modifiqué el sistema para que los usuarios `jedi1` y `sith1` no aparezcan en la ventana de inicio del sistema.
* Ya que el sistema usa AccountsService, modifiqué el fichero de cada usuario de la siguiente forma:
  * `/var/lib/AccountService/users/jedi1`
    > [User]
    >
    > System Account=true

  * `/var/lib/AccountService/users/sith1`
    > [User]
    >
    > System Account=true

![Ocultar Usuarios](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/os-ocult-us.png)

![Ocultar usuarios gráfico](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/os-ocultus-gr.png)

### 2.2. Claves seguras
Para empezar, configuré mi usuario y los usuarios `jedi1` y `jedi2` en el fichero `/etc/sudoers` para obtener privilegios administrativos.

![Sudoers](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/sudoers.png)

Modifiqué las claves de los usuarios de la siguiente forma:
* `sith1`: 1234
* `sith2`: casa
* `jedi1`: frodoHOBBITbolson
* `jedi2`: gandalfELGRIS

Tras esto, inicié la máquina con un CD-Live (knoppix).
* Monté la partición del disco duro que corresponde al SO GNU/Linux.
* Hice una copia de seguridad del fichero de claves con el comando: `cp /mnt/etc/shadow /mnt/etc/shadow.bak`.
* Creé el usuario `c3po` en knoppix con la clave `123456`.
* Copié la clave del usuario `c3po` del fichero `/etc/shadow` a los usuarios `jedi2` y `sith2` del fichero `/mnt/etc/shadow`.

![C3po](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/c3po.png)

Después, reinicie la Máquina Virtual sin el CD-Live de Knoppix y comprobé que se puede iniciar sesión en los usuarios `jedi2` y `sith2` con la clave `123456`.

![Jedi2 y Sith2](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/funciona.png)

### 2.3. Desactivar el inicio gráfico

Por último desactivé el inicio gráfico al inicio.
* Fue a `Administración de Servicios` dentro de `Yast`
* Una vez ahí, cambié `Estado predeterminado` de `Graphical Interface` a `Multi-User System`

![Multiusuario](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/multiusuario.png)

Ahora restauré el inicio gráfico automático.
* Ejecuté `yast`
* Y una vez dentro cambié `Multi-User System` por `Graphical Interface`

![](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/yast-comando.png)
