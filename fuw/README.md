
# Clonezilla device-device EFI

---

## 2. Preparativos

Escogemos una MV que ya tengamos instalada (en mi caso, OpenSUSE) y añadimos un seguno disco llamado `target-jorgesuarez24.vdi`.

![Añadir disco](./images/disco-target.png)

Tras esto descargar la ISO con Clonezilla más reciente.

---

## 3. Inicamos Clonezilla

Iniciar la MV con Clonezilla para realizar una clonación tipo `device-device` haciendo los siguientes pasos:

* Elegimos idioma

![Idioma](./images/idioma.png)

* Elegir el mapa de teclado `qwerty -> Standard -> Standard`

![Teclado](./images/teclado.png)

* Iniciar Clonezilla

![Iniciar](./images/start.png)

* `device-device`

![disco-disco](./images/disco-disco.png)

* `Begginer`

![Begginer](./images/begginer.png)

* `disco-local a disco-local`

![Local a Local](./images/local-local.png)

* Elegir disco origen

![Disco origen](./images/origen.png)

* Elegir disco destino

![Disco destino](./images/destino.png)

Tendrá que salir una pantalla como la siguiente cuando se esté copiando.

![Copiando](./images/copiando.png)

---

## 4. Comprobamos

Quitamos el `disco clonado` y creamos un archivo llamado `/home/jorge/Documentos/disco-original.txt`.

![Disco Original VB](./images/primer-disco.png)

![Disco Original](./images/disco-original.png)

Ahora quitamos el `disco original` y añadimos el `disco clonado`.

![Disco Clonado VB](./images/1disco.png)

Comprobamos que el fichero no existe

![No existe fichero](./images/disco-clonado.png)
