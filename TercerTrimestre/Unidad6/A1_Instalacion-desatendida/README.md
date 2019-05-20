
# Instalación desatendida de Windows7

---

## 1. Introducción

Vamos a crear una imagen ISO de Windows 7 con instalación desatendida. El sistema operativo se instalará en la máquina sin necesidad de que un usaurio supervise la instalación ya que todos los parámetros configurables son configuradas anteriormente en un archivo que incluiremos en la ISO llamado `autounattend.xml`

![Instalación desatendida](./images/instalacion-desatendida.png)

---

## 2. Instalar WAIK

### 2.1. Copiar ficheros

* Creamos la carpeta `C:\W7`.
* Montamos la ISO Windows 7 Enterprise de 64 bits en la unidad CD de la MV.
* Copiamos el contenido de la unidad de CD a la carpeta `C:\W7`.

![Copiar Archivos ISO Windows7](./images/copiar-w7.png)

### 2.2. Descargar e instalar WAIK

> Descargamos la ISO en la máquina real y la añadimos a la máquina de Windows7 donde creamos la carpeta `C:\W7`.

* Descargamos el Kit de instalación automatizada de Windows (AIK) para Windows 7.

![Windows Automated Instalation Kit 1](./images/descargar-waik.png)

* Instalamos la herramienta `WAIK`.

* Ir a `Administrador de imágenes del sistema de Windows` que se encuentra dentro de `Microsoft Windows AIK`. Ejecutar como administrador.

![Administrador de imágenes del sistema de Windows](./images/waik.png)

---

## 3. Crear fichero de respuestas

### 3.1. Abrir el archivo de catálogo

Ahora crearemos un catálogo que es el que nos dirá que tiene, que se puede  y no se puede hacer dentro de la imagen seleccionada de Windows 7.

* Vamos a `Archivo` -> `Seleccionar imagen de Windows` y buscamos el archivo siguiente:
  * `C:\W7\sources\install_Windows 7 ENTERPRISE.clg`.
* Nos saldrá en la esquina inferior izquierda una lista que podemos desplegar con diferentes componentes y paquetes.

![](./images/imagen-windows.png)

### 3.2.Crear el archivo de respuestas (autounattend.xml)

* Creamos el archivo de autorespuesta que configuraremos a continuación. Ir a `Archivo` -> `Nuevo archivo de respuesta`.
* Para agregar componentes hacemos lo siguiente:
  1. Buscamos los componentes en la parte izquierda.
  2. Hay que añadirlos en el ciclo que se indica
  3. Posteriormente completamos los valores de los parámetros asociados.

* Agregar los siguientes componentes al ciclo **windowsPE**

| **amd64-Microsoft-Windows-International-Core...neutral**
| ---
| **Parámetros** | **Configuración**
| InputLocale | es-ES
| System Locale | es-ES
| UILanguage | es-ES
| UserLocale | es-ES

```html
<table border="1">
  <tr>
    <th colspan="2">
     Celda de dos columnas
    </th>
  </tr>
  <tr>
     <td rowspan="2">
     Celda de dos filas
     </td>
     <td>
     Fila2,Columna2
     </td>
  </tr>
  <tr>
     <td>
     Fila3,Columna2
     </td>
  </tr>
</table>      
```

<table border="1">
  <tr>
    <th colspan="2">
     Celda de dos columnas
    </th>
  </tr>
  <tr>
     <td rowspan="2">
     Celda de dos filas
     </td>
     <td>
     Fila2,Columna2
     </td>
  </tr>
  <tr>
     <td>
     Fila3,Columna2
     </td>
  </tr>
</table>

![](./images/.png)

### 3.3. Validar y guardar respuestas




![](./images/.png)

---

## 4. Configurar aplicaciones



![](./images/.png)

---

## 5. Validar y guardar



![](./images/.png)
