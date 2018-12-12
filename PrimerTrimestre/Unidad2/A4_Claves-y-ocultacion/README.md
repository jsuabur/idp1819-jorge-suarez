
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

### 2.2. Claves seguras
Para empezar, configuré mi usuario y los usuarios `jedi1` y `jedi2` en el fichero `/etc/sudoers` para obtener privilegios administrativos.

Modifiqué las claves de los usuarios de la siguiente forma:
* `sith1`: 1234
* `sith2`: casa
* `jedi1`: frodoHOBBITbolson
* `jedi2`: gandalfELGRIS

### 2.3. Desactivar el inicio gráfico

Por último desactivé el inicio gráfico al inicio.
* Fue a `Administración de Servicios` dentro de `Yast`
* Una vez ahí, cambié `Estado predeterminado` de `Graphical Interface` a `Multi-User System`

![Multiusuario](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/multiusuario.png)

Ahora restauré el inicio gráfico automático.
* Ejecuté `yast`
* Y una vez dentro cambié `Multi-User System` por `Graphical Interface`

![](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A4_Claves-y-ocultacion/images/yast-comando.png)
