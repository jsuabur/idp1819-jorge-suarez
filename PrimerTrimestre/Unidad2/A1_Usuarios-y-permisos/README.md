
# Usuarios y permisos

---

## 1. SO Windows 7

### 1.1. Usando el GUI Windows

Creé el grupo `jedis` y dentro los usuarios `jedi1` y `jedi2`, incluidos también en el grupo de `administradores`.

![Grupo Jedis](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/jedis.png)

Tras esto, en el usuario `jedi1` creé tres carpetas con los siguientes permisos:
* `private`: *jedi1* control total y nadie más tiene permisos.
* `group`: *jedi1* control total y *jedis* permisos de lectura.
* `public`: *jedi1* control total y todos tienen permiso de lectura.

> Carpeta **private**

![Carpeta Private-Jedi1 Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/private-jedi1-w.png)

> Carpeta **group**

![Carpeta Group-Jedi1 Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/group-jedi1-w.png)

![Carpeta Group-Jedis Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/group-jedis-w.png)

> Carpeta **public**

![Carpeta Public-Jedi1 Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/public-jedi1-w.png)

![Carpeta Public-Jedis Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/public-todos-w.png)

### 1.2. Usando los comandos Windows

Creé el grupo `siths` y puse a `sith1` y `sith2` dentro del grupo y tambien de `usuarios`.

![Usuarios/Grupos Comandos Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/users-siths-w.png)

Después, creé tres carpetas con los siguientes permisos:
* `private`: Sólo *sith1* tiene control total.
* `group`: *sith1* tiene control total y *siths* permiso de lectura.
* `public`: *sith1* tiene control total y todos tienen permiso de lectura.

![Carpetas Siths Windows](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/permisos-comandos-w.png)

---

## 2. SO GNU/Linux OpenSUSE

### 2.2. Usando el GUI GNU/Linux

Creé el grupo `jedis` y dentro los usuarios `jedi1` y `jedi2`.

Para cada usuario creé las siguientes tres carpetas con los siguientes permisos:
* `private`: Solo *jedi1* tiene todos los permisos.
* `group`: *jedi1* tiene todos los permisos y el grupo *jedis* permisos de lectura/ejecución.
* `public`: *jedi1* tiene todos los permisos y todos tienen permisos de lectura/ejecución.

> Carpeta **private**

![Carpeta Private-Jedi1 OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/private-jedi1-os.png)

> Carpeta **group**

![Carpeta Group-Jedi1 OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/group-jedi1-os.png)

> Carpeta **public**

![Carpeta Prublic-Jedi1 OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/public-jedi1-os.png)

### 2.3. Sudoers (Grupo privilegiado)

Para dar permisos de superusuario a los miembros del grupo `jedis` edité el fichero de configuración */etc/sudoers* añadiendo la línea:

> %jedis ALL = (root) NOPASSWD:ALL

![Sudoers Jedis](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/jedis-sudoers.png)

Para comprobarlo, entré con `jedi1` y ejecuté el comando *`sudo -l`* para consultar la configuración de sudoers.

![Comando Sudoers Jedis](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/sudo-l-jedis.png)

### 2.4. Usando los comandos

Creé los usuarios `sith1` y `sith2` dentro del grupo `siths`. Tras esto, creé las carpetas *private*, *group* y *public*, con los siguientes permisos:
* `private`: *sith1* tienen todos los permisos.
* `group`: *sith1* tienen todos los permisos y *siths* tiene permisos de lectura/ejecución.
* `public`: *sith1* tienen todos los permisos y todos tienen permisos de lectura/ejecución.

![Carpetas-Siths Comandos OpenSUSE](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/permisos-sith1-os.png)

### 2.5. Configurar sudoers para el otro grupo

Para dar permisos de superusuario a los miembros del grupo `siths` edité el fichero de configuración */etc/sudoers* añadiendo la línea:

> %siths ALL = (root) NOPASSWD:/sbin/shutdown, /sbin/fdisk -l, /sbin/ifconfig

![Sudoers Siths](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/siths-sudoers.png)

Para comprobarlo, entré con sith1 y ejecuté el comando *`sudo -l`*, *`sudo fdisk -l`* y *`sudo ifconfig`* para consultar la configuración de sudoers.

![Sudo -l Siths](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/sudo-l-sith1.png)

![Sudoers Siths](https://github.com/jsuabur/idp1819-jorge-suarez/blob/master/PrimerTrimestre/Unidad2/A1_Usuarios-y-permisos/images/sudo-ifconfig.png)
