
# PDC Políticas o directivas de grupo

---

## 2. Aplicar directivas de Usuario

### 2.1. Crear las OU y GPO

**IMPORTANTE** Antes de empezar la práctica crearemos una "snapshot" del PDC, para prevenir futuros problemas.

> **IMPORTANTE**: No aplicar la directivas a todo el dominio. SÓLO a las unidades organizativas que se especifiquen. Un error grave es aplicar las directivas a todo en lugar de a cada OU. Este error puede afectar al correcto funcionamiento del servidor.

Unidades Organizativas | `jedis24c1819` | `siths24c1819`
:--------------------- | :------------: | :------------:
**Usuarios**       | `obiwan` y `yoda`  | `vader` y `maul`
**GPO**                | `gpo_jedis24`  | `gpo_siths24`

**Unidades Organizativas**

![Unidades Organizativas](./images/ou-jedis24c1819.png)

![Unidades Organizativas](./images/ou-siths24c1819.png)

**GPO**

![Unidades Organizativas](./images/jedis24-siths24.png)

### 2.2. Personalizar cada GPO de forma diferente

> INFO Para editar configuraciones de Directiva de grupo:
>
> * En Group Policy Management (Administración de directivas de grupo), en el árbol de consola, desplegar Group Policy Objects (Objetos de Directiva de grupo). Click con el botón derecho del ratón en el GPO y seleccionar Edit (Editar).
> * En el Editor de objetos de Directiva de grupo, buscar la Directiva de grupo que queremos modificar y hacemos doble clic. En el cuadro de diálogo Propiedades, cambiamos la configuración y Aceptar.

Ahora aplicaremos y habilitaremos las siguientes directivas a las OU anteriores.
* Encontraremos todas las siguientes dentro de `Configuración de usuario / Directivas / Plantillas administrativas`

![Carpeta administrativa](./images/carpeta-directivas.png)

#### OU jedis24c1819

| Menú Inicio y barra de tareas
| :-----------------------------------------:
| `Quitar el menú Ejecutar del menú Inicio`
| `Quitar el icono Red del menú Inicio`
| `Quitar icono de red`
| `Quitar Conexiones de red del menú Inicio`

#### OU siths24c1819

| Panel de Control
| :---------------------------------------:
| `Prohibir el acceso al Panel de control`

| Escritorio
| :-----------------------------------------:
| `Ocultar el icono Ubicaciones de red del escritorio`

| Componentes de Windows / Explorador de Windows
| :---------------------------------------------:
| `Quitar "Conectar a unidad de red" y "Desconectar de unidad de red"`

### 2.3. Comprobar que se aplican las directivas

Al terminar de configurar las directivas, haremos lo siguiente:
* Abrir consola como administrador y ejecutar `gpupdate /force` para forzar las actualizaciones de las directivas.

> En algunos casos, después de definir una política, ésta tarda un tiempo en activarse, pero usando el comando anterior, nos aseguramos de que este paso de activación se realice inmediatamente.

![gpupdate /force](./images/gpupdate-force.png)

* Ir a `Administración de Directivas de Grupo` y comprobar el resumen de la configuración de cada una de las directivas creadas.

**GPO jedis24**

![GPO jedis24c1819](./images/gpo_jedis24-directivas.png)

**GPO siths24**

![GPO siths24](./images/gpo_siths24-directivas.png)

* Ahora comprobamos los efectos de las directivas de usuario en las MV clientes.

**Cliente 1**

Comprobamos en el `Cliente 1` con un usuario de la OU `jedis24c1819`, en mi caso `obiwan`.

![Políticas Obiwan](./images/politicas-obiwan.png)

**Cliente 2**

Después comprobamos en el `Cliente 2` con un usuario de la OU `siths24c1819`, en mi caso `maul`.

![Políticas Maul](./images/politicas-maul.png)

---

## 3. Aplicar directiva de Equipo

### 3.1. Crear recurso compartido de red

* Creamos la carpeta `e:\software24`

Permisos | **`Usuarios del dominio`** | **`Administradores`**
-------- | :------------------------: | :-----------:
Control total |    |   &#x2714;
Modificar |             | &#x2714;
Lectura y ejecución |        &#x2714;         | &#x2714;
Mostrar el contenido de la carpeta |     &#x2714;     | &#x2714;
Lectura |       &#x2714;         | &#x2714;
Escritura |             | &#x2714;
Permisos especiales |             | &#x2714;

![Permisos Usuarios del dominio](./images/ud-permisos-carpeta.png)

![Permisos Administradores](./images/admins-permisos-carpeta.png)

* Creamos el recurso compartido de red `software24` a la carpeta anterior

Permisos |        **`Todos`**         | **`Usuarios del dominio`**
-------- | :------------------------: | :------------------------:
Control total |                       |       &#x2714;
Cambiar |                             |       &#x2714;
Leer |         &#x2714;               |       &#x2714;

![Permisos Recurso de Red - Usuarios del dominio](./images/ud-permisos-recursos.png)

![Permisos Recurso de Red - Administradores](./images/todos-permisos-recursos.png)

* Creamos la subcarpeta `E:\software24\firefox`.

### 3.2. Instalar en el servidor

Ahora vamos a crear nuestro propio paquete de instalación MSI.

* Descargamos e instalamos el programa `WinINSTALL`.

![WinINSTALL](./images/WinINSTALL.png)

* Una vez instalada la aplicación hemos de asignar permisos de acceso al recurso compartido de WinINSTALL al usuario `Administrador` en modo `Leer`.

![Permisos Recurso de Red WinINSTALL - Administrador](./images/admin-permisos-winrec.png)

### 3.3. Crear paquete MSI

**En el cliente**

* Entramos con el usuario administrador del dominio
* Descargamos el instalador de Firefox.

> **¡OJO!** Sólo descargar. No instalar todavía. El instalador de Chrome debe tener un tamaño de varios MBs. Si tiene pocos KBs no es el instalador, sino un programa para descargar el instalador.

![Instalador Firefox](./images/instalador-firefox.png)

* Iniciamos la aplicación WinINSTALL LE de forma remota ejecutando `\\172.18.24.21\WinINSTALL\Bin\Discover.exe`

![Ejecutar WinINSTALL forma remota](./images/ejecutar-discover.png)

* Indicamos el nombre que vamos a asociar al paquete MSI y la ruta de red donde almacenaremos el MSI, en nuestro caso:
  * Nombre: `firefox24.msi`
  * Ruta de red: `\\172.18.24.21\software24\firefox\firefox24.msi`

![Paquete MSI Firefox](./images/firefox24.png)



### 3.4. Crear nueva GPO en el servidor



![](./images/.png)

### 3.5. Comprobar desde los clientes



![](./images/.png)
