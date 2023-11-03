---
enableLinks: true
slideNumber: true
theme: beige
---

# Bienvenidxs a ROS2


---

## ⚡Super Fast Linux Terminal Review⚡

---

### ¿Por Qué Necesitamos la Terminal?

La terminal es la manera de poder hablar con `ros2`:

```sh
$ ros2 run rasp_pkg raspberry_node.py
```

```sh
$ ros2 topic echo /speed_rpm
```

```sh
$ colcon build --symlink-install --packages-select rasp_pkg
```

Estos son algunos de ejemplos de commandos en `ros2`

---

<!-- .slide: data-auto-animate -->
### ⚡🚢Navegación En File System

---

<!-- .slide: data-auto-animate -->
### ⚡🚢Navegación En File System

- `pwd`: *Print working directory* Te dice en que ubicación estás
- `ls`: *list* Te puestra los archivos y los directorios
- `cd <directory>`: *Change directory* te mueve al directorio que le pongas
- `mkdir <directory>`: Crea un directorio en el `pwd`
- `rmdir <directory>`: Elimina un directorio vacío
- `touch <filename>`: Crea un archivo en el `pwd`
- `rm <filename>`: Elimina un archivo

note:

Mostrar los comandos de linux

Puedes hacer el siguiente ejemplo:

1. Abres la terminal en el `~`
2. Listeas el contenido
3. Te metes a `Documents`
4. Crear una carpeta `documentos_personales`
4. Crear una carpeta `codigo_taller`
5. Hacer un archivo `main.py`
5. Hacer un archivo `test.py`
6. Borrar archivo `test.py`
7. Editarlo `main.py` con `code`
8. Salirte de la carpeta `codigo_taller`
9. Borrar `documentos_personales`
10. Borrar `codigo_taller`

```sh
# Init terminal
$ pwd
/home/edy
$ ls
Desktop  Documents  Downloads  snap
$ cd Documents/
$ ls
$ mkdir documentos_personales
$ mkdir codigo_taller
$ cd codigo_taller/
$ pwd
/edy/Documents/codigo_taller
$ ls
$ touch main.py
$ touch test.py
$ ls
main.py  test.py
$ code main.py
$ rm test.py
$ cd ..
$ rmdir documentos_personales/
$ rmdir codigo_taller/
rmdir: failed to remove 'codigo_taller/': Directory not empty
$ rm -rf codigo_taller/
$ ls
```

Estas son las notas de la investigación

![[Introduccion a Linux#Navegación Por El FileSystem]]

---

<!-- .slide: data-auto-animate -->
### ⚡⚙Agregar Configuraciones

---

<!-- .slide: data-auto-animate -->
### ⚡⚙Agregar Configuraciones

Cuando se abre la terminal, se leen las configuraciones en el `.bashrc` y luego empieza *la session*

![[Introduccion a Linux#^98a36b]]

Para leer las configuraciones se usa el comando `source`

note:

Si los usuarios no están usando bash, comentar que puede ser `.zhrc` o algo parecido

---

<!-- .slide: data-auto-animate -->
### ⚡⚙Agregar Configuraciones


Puedes agregar más configuraciones en *la sessión* usando el comando de `source`

```sh
# Init terminal
$ source ~/.bashrc
$ source ~/.config.sh
$ source ~/.install.sh

```


---

<!-- .slide: data-auto-animate -->
### ⚡⚙Agregar Configuraciones

![[Introduccion a Linux#^2d5420]] <!-- element style="width:130%; height:auto;" -->

Esto nos servirá para configurar `ros` cuando estemos usando la terminal

---

<!-- .slide: data-auto-animate -->
### ⚡🐍Python

---

<!-- .slide: data-auto-animate -->
### ⚡🐍Python

Puedes usar **Python** desde la terminal:

![[Introduccion a Linux#^a117d1]]

![[Introduccion a Linux#^dd2dba]]

note: 

Hacer un ejemplo de un `hello world`

**main.py**

```python
def main():
  print("hello world!!")

if __name__ == "__main__":
  main()
```

---

<!-- .slide: data-auto-animate -->
### ⚡🐍Python

También puedes crear **ambientes virtuales** en python:

![[Python#^0152ce]]

Se crea una carpeta `.venv` con las dependencias de python

%% No se si se tiene que mostrar esto! %%

note: 

Hacer los comandos que vienen en la presentacion

---

<!-- .slide: data-auto-animate -->
### ⚡🐍Python

Para *activar* el ambiente virtual, usamos el comando: 

![[Python#^87b519]]

Con esto, nuestro `python` cambia a usar el de la carpeta `.venv`

%% No se si se tiene que mostrar esto! %%

note: 

1. Activa el ambiente virual
2. Decir que ahora puedes usar `python normal`

---
<!-- .slide: data-auto-animate -->
# ROS 2🤖

---
### ¿Qué es y para qué sirve? (esto lo hace edy)
---
### Workspaces (lo hace garza)
---
### Funcionamiento general

Esquemática general ejemplo del funcionamiento de ROS2
![[diagrama_ejemplo_ros2.png|500]]
Funcionamiento:
1. Se crea un *Nodo* con un *Publisher*
2. Se crea un *Nodo* con un *Subscriber*
3. *Publisher* manda *mensajes* a un *topic*
4. *Subscriber* recibe los *mensajes* del mismo *topic*
Un mismo nodo puede tener tantos publishers y subscribers como se desee
---
### Paquetes
Conjunto de nodos que forman una red en ROS2
```bash
cd ~/ros2_ws/src

# Creación del paquete llamado ros2_pkg de tipo python
ros2 pkg create ros2_pkg --build-type ament_python --dependencies rclpy
cd ..
colcon build --packages-select ros2_pkg

# Configuración para que ROS2 detecte el paquete
source .bashrc
```
---
### Topics y Messages 

![[topics.png|900]]
Los *Topics* son los canales por los nodos se comunican.
Toda la información que fluye por el *topic* debe estar en formato de un *message*.

---
### Topics y Messages
![[ejemplo_mensaje.png|650]]
Los *mensajes* son el tipo de **toda la información** que fluye en el *topic*. 

Se declaran en un *package* separado y se importan. 

---
## ¿Cómo crear un nodo?
### Pasos
1. Ir al source del workspace
```bash
# Ir al src del ws
cd ~/ros2_ws/ros2_pkg/src/ros2_pkg/ros2_pkg

```
2. Crear el archivo .py y configurarlo como ejecutable
```bash
touch node_name.py
chmod +x node_name.py
cd ..
```
---
3. Añadir el ejecutable a ROS2 en *setup.py*
4. Editar el nodo: Tomar como base la template
5. Regresar al directorio del workspace y hacer *colcon build*
```bash
cd ~/ros2_ws
colcon build --packages-select ros2_pkg --symlink-install
```
%% Mencionar qué es packages-select y symlink-install Mostrar el código de ejemplo y de añadir el ejecutable desde la VM. El ejemplo de código lo va a mostrar garza%%

---
# Template de nodo (garza)

---
### Interfaces
ros2 topic list
ros2 topic info /topic
ros2 interface show /interface
ros2 interface list

---
### Crear una interfaz (garza)
---
### Ejemplo práctico
Hagamos un caso 
