
# PDC Windows Server

---

## 1. Preparativos



---

## 2. Instalar el Controlador de dominio

**Instalar en Windows 2008 Server**

* En Windows 2008 Server podemos abrir una consola `cmd` y ejecutar el comando `dcpromo`.

* Se inicia el asistente de configuración de los servicios del dominio de AD (Active Directory). Ponemos los siguientes valores:
  * No marcamos *`Modo avanzado`*
  * Marcamos *`Crear un dominio nuevo de un bosque nuevo`*
  * FQDN del dominio raíz del bosque: *`burgos24dom.curso1819`*
  * Nivel funcional del bosque: *`Windows Server 2008`*
  * Dejamos marcado *`Servidor DNS`*
  * Carpetas de almacenamiento *`Dejar valores por defecto`*
  * Ponemos una contraseña para el Administrador del dominio.


![Windows Server 2008 Funcional](./images/2008-funcional.png)

* En la pestaña `Resumen` comprobamos que hemos puesto todo correctamente y reiniciamos.

![Resumen Servicios de dominio](./images/resumen-dominio.png)

**Comprobaciones**

* Vamos a `DNS` dentro de `Herramientas` para comprobar que aparece dentro de `Zona de búsqueda directa` nuestro dominio.
* Abrir una consola y ejecutar `nslookup burgos24dom.curso1819`. Debe aparecer la IP de nuestro servidor PDC.

![Comprobación DNS comandos](./images/DNS-consola.png)

---

## 3. Usuarios del dominio

### 3.2. Práctica

Vamos a crear usuarios y grupos del dominio:

* Ir a `Usuarios y Equipos de Active Directory`

Grupo | `jedis1819`
------|-----------
**Ámbito** | Global
**Tipo** | Seguridad
**Usuarios de dominio** | `yoda` y `obiwan`

![Grupo jedis1819](./images/jedis1819.png)

Grupo | `siths1819`
------|-----------
**Ámbito** | Global
**Tipo** | Seguridad
**Usuarios de dominio** | `vader` y `maul`

![Grupo siths1819](./images/siths1819.png)

* No confundir usuarios locales con usuarios del dominio.

![Grupos y usuarios](./images/grupos.png)

---

## 4. Equipos del dominio

### 4.1. Preparativos



### 4.2. Problemas en la unión al dominio



### 4.3. Comprobaciones

**Por entorno gráfico**



**Por comandos**



---

## 5. Perfiles móviles

### 5.1. Crear un segundo disco



### 5.2. Crear Perfiles de usuarios



### 5.3. Limpiar el equipo cliente



---

## 6. Perfiles obligatorios



---

## 7.Control de tiempo
* Modificamos los permisos de acceso a los usuarios del dominio, de la siguiente forma:
  * Los `"jedis"` sólo pueden acceder de *08:00 - 14:00* (de lunes a viernes)

![Horario jedis](./images/.png)

  * Los `"siths"` sólo pueden acceder de *14:00 - 20:00* (de lunes a viernes)

![Horario siths](./images/.png)
