
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
    * Añadimos un disco extra de 10GB y lo configuramos en la unidad `E:`.

![Configuración Windows Server 2008](./images/windows-server.png)

* 1 MV Windows 7. La configuramos como en la foto.

![Configuración Windows7](./images/windows.png)

---

## 2. Servidor WSUS

**MV Windows Server**

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



![](./images/.png)

### 2.3. Configuración del servidor



![](./images/.png)

### 2.4. Servicio con inicio automático



![](./images/.png)

---

## 3. Cliente WSUS

### 3.1. Teoría



![](./images/.png)

### 3.2. Configurar el cliente

**Configurar sin PDC**

![](./images/.png)

### 3.3. Comprobación



![](./images/.png)

### 3.4. Servicio en el cliente



![](./images/.png)

### 3.5. En el caso de tener PROBLEMAS

**Sólo en caso de tener problemas de conexión del cliente WSUS con el servidor.**

* Descargar y ejecutar Herramienta de diagnóstico WSUS desde línea de comandos.
* Algunos problemas de cliente WSUS se solucionan con la siguiente herramienta:
  * Descargar herramienta Solucionador WSUS
  * https://support.microsoft.com/es-es/help/10164/fix-windows-update-errors
* `sfc /scannow`, repara archivos dañados.

> Imagen de EJEMPLO
![Herramienta diagnostico WSUS](./images/herram-wsus.png)

---

## 4. Auditar procesos

### 4.1. Auditar desde el servidor



![](./images/.png)
