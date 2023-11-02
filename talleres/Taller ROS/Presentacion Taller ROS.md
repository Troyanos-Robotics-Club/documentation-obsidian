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

Para *activar* el ambiente virual, usamos el comando: 

![[Python#^87b519]]

Con esto, nuestro `python` cambia a usar el de la carpeta `.venv`

%% No se si se tiene que mostrar esto! %%

note: 

1. Activa el ambiente virual
2. Decir que ahora puedes usar `python normal`

---
<!-- .slide: data-auto-animate -->
### Workspaces

El workspace es donde se va a hacer todo el código de la aplicación
Para crear un workspace se hace lo siguiente

```bash
cd
mkdir ros2_ws
cd ros2_ws
mkdir src
colcon build
```

Ahora el ros2_ws debe contener 4 folders:
-build
-install
-log
-src

---
Ahora se requiere hacer source del ~/ros2_ws/install/setup.bash para que cada vez que se abra la terminal se detecte este workspace

Para hacer source y agregarlo al bashrc se puede correr el siguiente comando:

```bash
cd
source ~/ros2_ws/install/setup.bash && echo "source ~/ros2_ws/install/setup.bash" >> .bashrc
```

Para confirmar que todo el environment de ROS2 esté configurado correctamente, corre el siguiente comando:
```bash
cd
gedit ~/.bashrc
```

Ve hasta abajo del documento y se deben ver las siguientes 3 líneas:

![[Pasted image 20231101215019.png]]