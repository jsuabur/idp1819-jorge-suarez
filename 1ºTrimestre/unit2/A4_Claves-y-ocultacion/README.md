
# Claves y ocultación

---

## 1. SO Windows

### 1.1. Ocultación de usuarios

Modifiqué la configuración del sistema para que los usuarios `jedi1` y `jedi2`, no aparezcan en la ventana de inicio del sistema, de la siguiente forma:
* Inicié sesión con una cuenta de administrador.
* Ejecuté registry con el comando `regedit`.
* Exporte una copia de seguridad antes de cambiar la configuración.

![Ejecutar Registry](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/1%C2%BATrimestre/unit2/A4_Claves-y-ocultacion/images/regedit.png)

Tras ejecutarlo entre en la carpeta  `HKLM\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Winlogon\` e hice lo siguiente:
* Cree una llave *(carpeta)* con el nombre: `SpecialAccounts`
* Dentro otra llave llamada: `UserList`
* Y en esta última creé dos registros de tipo `DWORD` con los nombres de las cuentas que quería ocultar:
  * `jedi1`
  * `jedi2`

![UserList](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/1%C2%BATrimestre/unit2/A4_Claves-y-ocultacion/imagesUserList.png)

Para acabar con la parte de ocultación de Windows, reinicie la MV y comprobé satisfactoriamente que se ocultaron los usuarios `jedi1` y `jedi2`.

![Jedis Ocultos](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/1%C2%BATrimestre/unit2/A4_Claves-y-ocultacion/images/jedis-ocult.png)

### 1.2. Modo de incio de sesión seguro



### 1.3. Claves seguras



---

## SO GNU/Linux



### 2.1. Ocultar usuarios



### 2.2. Claves seguras



### 2.3. Desactivar el inicio gráfico
