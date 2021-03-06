
# Servidor de actualizaciones

---

## 1. WSUS (Windows Server Update Services)

### 1.1. Teoría

Inconvenientes de no tener nuestros sistemas actualizados:
* Un atacante puede aprovechar las vulnerabilidades.
* Aumenta el tiempo de inactividad de los PC's comprometidos.
* La información de la empresa puede verse comprometida.

Ventajas de tener un servidor WSUS que almacena y distribuye las actualizaciones de software MS:
* Reducción del consumo del ancho de banda WAN.
* Mejora de los tiempos de actualización global.
* Mayor control de las actualizaciones que se desean.
* Servidor pone las actualizaciones disponibles a los clientes.
* El administrador del servidor aprueba y prioriza las actualizaciones.
* El cliente se conecta a WSUS e instala los paquetes usando Windows Update.

> **Resumen:**
>
> * WSUS proporciona control a la hora de aprobar y distribuir actualizaciones de Microsoft entre sus ordenadores clientes.
> * Un servidor WSUS puede copiar actualizaciones desde Microsoft y almacenarlas localmente. Entonces, los ordenadores clientes descargarán las actualizaciones desde su servidor WSUS en vez de descargarlas desde Microsoft a través de Internet.
> * Para soportar organizaciones con muchas oficinas, los servidores WSUS de descarga pueden sincronizar actualizaciones, aprobaciones y opciones de configuración de los servidores WSUS de subida.
> * WSUS también requiere IIS.

![WSUS Esquema Ejemplo](./images/wsus-croquis.png)

### 1.2. Preparativos

Vamos a necesitar 2 MVs.
* 1 MV Windows Server 2008. La configuramos como en la foto.

  ![Configuración Windows Server 2008](./images/conf-server.png)

  * Añadimos un disco extra de 10GB y lo configuramos en la unidad `E:`.

  ![Disco Extra Windows Server 2008](./images/disco-server.png)

* 1 MV Windows 7. La configuramos como en la foto.

![Configuración Windows7](./images/conf-windows.png)

---

## 2. Servidor WSUS

**MV Windows Server**
> Todo este apartado (2.1. / 2.2. / 2.3. / 2.4.) lo haremos con el Windows Server.

### 2.1. Teoría

Consideraciones a tener en cuenta:
* NO es necesario tener un `Active Directory` para montar el servicio WSUS.
* Servidor WSUS se conecta vía `HTTP/HTTPS` con el exterior. Se usa `IIS` en WSUS para que se conecten los clientes.
* Se requiere al menos 6GB de disco duro para almacenar las actualizaciones.
* Tendremos que hacer copias de seguridad de la BBDD de WSUS periódicamente.
* Necesitamos 1 servidor WSUS por cada 10 PC's. En caso de fallo disponemos de 1 semana para reemplazar el servidor.
* Podremos usar como fuente origen de las actualizaciones a los servidor de Microsoft u otros servidores WSUS.
* La base de datos que guarda la información, la podemos tener en `C:\WSUS\UpdateServicesDbFiles\SUSDB.mdf` (WS2008) o montar un SQL-Server.
* En nuestro caso lo vamos a hacer SIN SQL-Server.

### 2.2. Instalación del servidor

* Nos aseguramos de que tenemos la instalación en estado `No ilegal`.
* Utilizaremos la forma más sencilla para instalar el software WSUS, que es usar la propia herramienta de administrar del servidor Windows Server.
  * `Administrador del servidor` -> `Roles` -> `Agregar roles` - > `WSUS`.

![Administrar el servidor](./images/server-wsus.png)

### 2.3. Configuración del servidor

En WS2008 vamos a `WSUS` -> `Opciones` -> `Asistente para la configuración del servidor WSUS`, para ir a la configuración de WSUS.

Configuramos servidor WSUS con los siguientes parámetros:
* No usar base de datos
* Almacenar actualizaciones en `E:actualizaciones24`.
* Selección de Productos: Para minizar descargas es conveniente hacer una selección de idiomas y de productos concretos para actualizar. Elegir:
  * Idioma: `Español` e `Inglés`.

![Idioma del producto](./images/idioma-wsus.png)

  * Producto: `Windows7`.
  * Tipo de actualización: `Actualizaciones críticas` y `Actualizaciones de seguridad`.
* Fuente de sincronización: `Microsoft` (Windows Update).
* Elegimos sincronización manual en lugar de automática. Elegimos manual para hacer nuestras pruebas de clase. Cuando estemos en la empresa elegiremos sincronización automática.
* Iniciar sincronización inicial.

![Iniciamos sincronización inicial](./images/sincr-inicial.png)

Aprobamos algunas actualizaciones del Windows 7, en el servidor WSUS:
* Ir a `Administración del servidor` -> `Windows Server Update Services` -> `Update Services` -> `Actualizaciones` -> `Actualizaciones críticas`.
  * Seleccionamos 3 actualizaciones y las aprobamos.
* `Windows Server Update Services` -> `Update Services` -> `Sincronizar` para conectarnos con los servidores de Microsoft y comenzar la descarga de los paquetes aprobados.

![Actualizacion Windows7](./images/act-windows.png)

### 2.4. Servicio con inicio automático

Nos aseguramos en `Administración` -> `Servicios` que el servicio WSUS tiene configurado inicio automático al arrancar la máquina.

![Inicio automático](./images/ini-auto.png)

---

## 3. Cliente WSUS

### 3.1. Teoría

Parámetros de configuración en el cliente:
* Máquina Servidor WSUS
* Frecuencia, notificaciones, grupo asignado.
* Reinicio: automático / confirmación / retrasar
* Administración de energía: Iniciar PC si está apagado para ejecutar actualización.

### 3.2. Configurar el cliente

#### Configurar sin PDC

**Configuración usando Políticas de Grupo (Local)**

* En `Especificar la ubicación del servicio Windows Update en la intranet`:
  * En WS2008 se usan los puertos 80/443. Entonces hay que poner `http://172.18.24.22`, en mi ejemplo.
* Ejecutar `gpupdate /force` en una consola como administrador. Este comando fuerza a que se apliquen los cambios realizados en las directivas.

![Habilitar el servidor](./images/habilitar.png)

### 3.3. Comprobación

Para comprobarlo, hay varias formas, aunque yo utilizaré la siguiente:

**Comprobación 1**

* Ejecutamos la siguiente consulta de registro en línea de comandos:
  * `reg query HKLM\SOFTWARE\Policies\Microsoft\Windows\WindowsUpdate`
* Se muestran parámetros de configuración del servidor WSUS en pantalla

![Comprobación](./images/comp1-33.png)

### 3.4. Servicio en el cliente

* Cuando cambiamos la configuración, hay que reiniciar Windows Update en el cliente:

* `net stop wuauserv` para parar el servicio de Windows Update.
* `net start wuauserv` para iniciar el servicio de Windows Update.

Invocaremos los siguientes comandos para que Windows Update conecte con el servidor:

* `wuauclt.exe /detectnow`
* `wuauclt /a`

![Detectar equipo](./images/detectar.png)

### 3.5. En el caso de tener PROBLEMAS

**Sólo en caso de tener problemas de conexión del cliente WSUS con el servidor.**

* Descargar y ejecutar Herramienta de diagnóstico WSUS desde línea de comandos.
* Algunos problemas de cliente WSUS se solucionan con la siguiente herramienta:
  * Descargar herramienta Solucionador WSUS.
  * https://support.microsoft.com/es-es/help/10164/fix-windows-update-errors
* `sfc /scannow`, repara archivos dañados.

> Imagen de EJEMPLO
![Herramienta diagnostico WSUS](./images/herram-wsus.png)

---

## 4. Auditar procesos

### 4.1. Auditar desde el servidor

* Vamos a la MV del servidor WSUS.
* Ir a `Herramientas` -> `WSUS` -> `Equipos`.

![Actualizaciones](./images/actualizar.png)
