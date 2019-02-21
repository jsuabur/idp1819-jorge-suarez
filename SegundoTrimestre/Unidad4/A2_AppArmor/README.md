
# AppArmor

---

## 1. AppArmor: Teoría/explicación

### 1.1. Modos de trabajo

**Modos de trabajo**

* `complain/learning` Modo de queja/aprendizaje
* `enforce` Fuerza la aplicación de las políticas/reglas.

**Control de servicio AppArmor**

* `systemctl status apparmor` Ver el estado del servicio.
* `systemctl start apparmor` Iniciar el servicio.
* `systemctl stop apparmor` Parar el servicio.
* `systemctl enable apparmor` Activar inicio automático.
* `systemctl disable apparmor` Desactivar inicio automático.

### 1.2. Yast



### 1.3. Los perfiles



---

## 2. AppArmor: Práctica

### 2.1. Preparativos

> En la `Terminal 1`



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
