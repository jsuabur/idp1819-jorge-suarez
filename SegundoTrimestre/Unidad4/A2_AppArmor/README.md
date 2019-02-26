
# AppArmor

---

## 1. AppArmor: Teoría/explicación

### 1.1. Modos de trabajo

**Modos de trabajo**

* `complain/learning` Modo de queja/aprendizaje
* `enforce` Fuerza la aplicación de las políticas/reglas.

**Control del servicio AppArmor**

* `systemctl status apparmor` Ver el estado del servicio.
* `systemctl start apparmor` Iniciar el servicio.
* `systemctl stop apparmor` Parar el servicio.
* `systemctl enable apparmor` Activar inicio automático.
* `systemctl disable apparmor` Desactivar inicio automático.

### 1.2. Yast

* La gestión de los perfiles AppArmor con Yast `Yast -> Configuración AppArmor`, permite:
  * Cambiar la configuración de AppArmor.
  * Gestionar los perfiles existentes.
  * Crear un perfil manualmente.

### 1.3. Los perfiles

El perfil es una configuración de seguridad que establece que permisos tiene un determinado ejecutable.

Herramientas como `aa-genprof`, nos puede ayudar a crear el perfil:
  * Crear un perfil con `aa-genprof`
  * Crear un perfil con `aa-autodep`

---

## 2. AppArmor: Práctica

### 2.1. Preparativos

> En la `Terminal 1`

* Abrimos una sesión con nuestro usuario, en mi caso `jorge`.
* Copiamos el programa `/bin/cp` con el nuevo nombre `/home/jorge/aa/mycopy`.
* Crearemos lo siguiente:
  * Crear directorio `/home/jorge/aa/elhalcon/`
  * `elhalcon/han.txt` Escribir el contenido *jorge24*
  * `elhalcon/chewaka.txt` Escribir el contenido *jorge24*
  * `elhalcon/leia.txt` Escribir el contenido *jorge24*
  * Crear directorio `/home/jorge/aa/ciudad-nube/`
* Probamos a copiar archivos con nuestro comando `mycopy`:
  * `cd /home/jorge/aa/`
  * `./mycopy elhalcon/* ciudad-nube`
  * comprobamos el resultado -> `tree`

![Copiar elhalcon en ciudad-nube](./images/copia-halcon-nube.png)

* limpiamos el directorio con `rm ciudad-nube/*`

![](./images/copia-halcon-nube.png)

### 2.2. Generar el perfil

> En la `Terminal 2`



> En la `Terminal 1`



> En la `Terminal 2`



### 2.3. Comprobamos



---

## 3. Forzamos el perfil

### 3.1. Preparativos

> En la `Terminal 2`



> En la `Terminal 1`



### 3.2. Comprobamos

> En la `Terminal 2`



---

## 4. Modo queja

### 4.1. Perfil en modo queja

> En la `Terminal 2`



> En la `Terminal 1`



### 4.2. Comprobamos

> En la `Terminal 2`

* Consultamos el estado de los perfiles con `apparmor_status`
* Consultamos los eventos asociados a nuestro ejecutable con:
  * `ausearch -x mycopy | aureport -u`
  * `cat /var/log/audit/audit.log |grep mycopy`

![Ausearch 4.2.](./images/eventos-42.png)

![Eventos 4.2.](./images/cat-42.png)
