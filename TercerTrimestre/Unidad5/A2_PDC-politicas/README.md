
# PDC Políticas o directivas de grupo

---

## 2. Aplicar directivas de Usuario

**IMPORTANTE** Antes de empezar la práctica crearemos una "snapshot" del PDC, para prevenir futuros problemas.

> **IMPORTANTE**: No aplicar la directivas a todo el dominio. SÓLO a las unidades organizativas que se especifiquen. Un error grave es aplicar las directivas a todo en lugar de a cada OU. Este error puede afectar al correcto funcionamiento del servidor.

Unidades Organizativas | `jedis24c1819` | `siths24c1819`
:--------------------: | :-----------: | :------------:
**Usuarios**       | `obiwan` y `yoda` | `vader` y `maul`
**GPO**                | `gpo_jedis24` | `gpo_siths24`

> INFO Para editar configuraciones de Directiva de grupo:
>
> * En Group Policy Management (Administración de directivas de grupo), en el árbol de consola, desplegar Group Policy Objects (Objetos de Directiva de grupo). Click con el botón derecho del ratón en el GPO y seleccionar Edit (Editar).
> * En el Editor de objetos de Directiva de grupo, buscar la Directiva de grupo que queremos modificar y hacemos doble clic. En el cuadro de diálogo Propiedades, cambiamos la configuración y Aceptar.

Ahora aplicaremos las siguientes directas a las OU anteriores.
* Encontraremos todas las siguientes dentro de `Configuración de usuario / Directivas / Plantillas administrativas`

#### OU jedis24c1819

| Menú Inicio y barra de tareas
| :---------------------------:
| `Quitar el menú Ejecutar del menú Inicio`
| `Quitar el icono de Red del menú Inicio`
| `Quitar icono de Red`
| `Quitar Conexiones de red del menú Inicio`

#### OU siths24c1819



---

## 3. Aplicar directiva de Equipo

### 3.1. Instalar en el servidor



### 3.2. Crear paquete MSI



### 3.3. Crear nueva GPO en el servidor



### 3.4. Comprobar desde los clientes
