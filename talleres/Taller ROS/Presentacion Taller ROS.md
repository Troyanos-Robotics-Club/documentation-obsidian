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
# ROS2 🤖
---
Que es y para que sirve (Edy)

---
<!-- .slide: data-auto-animate -->
### Workspaces
El workspace es donde se va a hacer todo el código de la aplicación de ROS2

Para crear un workspace se hace lo siguiente
```bash
cd
mkdir ros2_ws
cd ros2_ws
mkdir src
colcon build
```
Ahora el ros2_ws debe contener 4 folders:

-build -install -log -src

---
Ahora se requiere hacer source del **~/ros2_ws/install/setup.bash** para que cada vez que se abra la terminal se detecte este workspace

Para hacer source y agregarlo al bashrc se puede correr el siguiente comando:

```bash
cd
source ~/ros2_ws/install/setup.bash && echo "source ~/ros2_ws/install/setup.bash" >> .bashrc
```
---
Para confirmar que todo el environment de ROS2 esté configurado correctamente, corre el siguiente comando:
```bash
cd
gedit ~/.bashrc
```

Ve hasta abajo del documento y se deben ver las siguientes 3 líneas:
``` gedit
source /opt/ros/humble/setup.bash
source ~/ros2_ws/install/setup.bash
source /usr/share/colcon_argcomplete/hook/colcon-argcomplete.bash
```

---
### Turtlesim 🐢

Turtlesim es un paquete ya incluido de ROS2 que tiene una versión simplificada de una simulación de un robot

Para instalar turtlesim corre el siguiente comando:

```bash
sudo apt install ros-humble-turtlesim
```

Ahora, asegúrate de tener todas las terminales sourceadas con

``` bash
source .bashrc
```

---
Para correr la interfaz de turtlesim corre lo siguiente en una terminal:

```bash
ros2 run turtlesim turtlesim_node
```

Ahora en una terminal diferente:

``` bash
ros2 run turtlesim turtle_teleop_key
```

---
Mientras estas en la terminal de teleopkey, puedes controlar la tortuga de la interfaz
![[Correr Turtlesim.png]]
---
Ahora para ver un ejemplo de lo que se puede llegar a hacer con esta simple aplicación, corre el siguiente comando

``` bash
cd
cd ~/ros2_ws/src/
git clone https://github.com/davidogarzas/taller_ros.git
cd ..
colcon build
source ~/ros2_ws/install/setup.bash
```

---
Ahora se requeriran 4 terminales. Para cada terminal, corre los siguientes comandos:

``` bash
ros2 run turtlesim turtlesim_node
```

``` bash
ros2 run turtle3 manager
```

``` bash
ros2 run turtle3 movement
```

``` bash
ros2 run turtle3 spawner
```

---

![[turtle_chaser.png]]

---
### Funcionamiento general

Esquemática general ejemplo del funcionamiento de ROS2

![[diagrama_ejemplo_ros2.png|500]]
---
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
Los *Topics* son los canales por los que los nodos se comunican.
Toda la información que fluye por el *topic* debe estar en formato de un *message*.

---
### Topics y Messages
![[ejemplo_mensaje.png|400]]
Los *mensajes* son el tipo de **toda la información** que fluye en el *topic*. 

Se declaran en un *package* separado y se importan. 

---
## ¿Cómo crear un nodo?

Ir al source del workspace
```bash
# Ir al src del ws
cd ~/ros2_ws/ros2_pkg/src/ros2_pkg/ros2_pkg

```
Crear el archivo .py y configurarlo como ejecutable
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
## Template Nodo
Un nodo se divide en dos partes principales

Esta es la sección que se edita para hacer el funcionamiento deseado
```python
import rclpy
from rclpy.node import Node

class NodeName(Node):
    def __init__(self) -> None:
        super().__init__('node_name')
        # Create Publishers
        # Create Subscribers
        # Initialize attributes
        # Create timers
    # Create callback methods (subscribers and timers)
```
---
Esta sección siempre es la misma para todos los nodos, lo único que hay que cambiar son:
- node_name
- NodeName()

```python
def main(args=None) -> None:
    rclpy.init(args=args)
    node_name= NodeName()
    rclpy.spin(node_name)
    node_name.destroy_node()
    rclpy.shutdown()
if __name__=='__main__':
    try:
        main()
    except Exception as e:
        print(e)
```
---
## Crear ejemplo de Nodo Publisher
Primero se crea un nuevo nodo llamado my_first_publisher.py
```bash
cd ~/ros2_ws/ros2_pkg/src/ros2_pkg/ros2_pkg
touch my_first_publisher.py
chmod +x my_first_publisher.py
```
---
### Copiar código de template al nuevo nodo y editar NodeName y node_name
``` python
import rclpy
from rclpy.node import Node

class MyFirstPublisher(Node):
    def __init__(self) -> None:
        super().__init__('my_first_publisher')
        # Create Publishers
        # Create Subscribers
        # Initialize attributes
        # Create timers
    # Create callback methods (subscribers and timers)
```
---
```python
def main(args=None) -> None:
    rclpy.init(args=args)
    my_first_publisher= MyFirstPublisher()
    rclpy.spin(my_first_publisher)
    my_first_publisher.destroy_node()
    rclpy.shutdown()
if __name__=='__main__':
    try:
        main()
    except Exception as e:
        print(e)
```
---
## Agregar ejecutable al setup.py
``` python
entry_points = {
	'console_scripts': [
			"MyFirstPublisher = ros2_pkg.my_first_publisher:main"
		],
}
```
---
## Agregar atributos (variables)
``` python
import rclpy
from rclpy.node import Node

class MyFirstPublisher(Node):
    def __init__(self) -> None:
        super().__init__('my_first_publisher')
        # Create Publishers
        # Create Subscribers
        # Initialize attributes
        self.counter = 0
        # Create timers
    # Create callback methods (subscribers and timers)
```
---
## Agregar Timers
Para crear un timer se requiere de dos partes:
- La variable que mantiene cuenta del tiempo
- El callback que se ejecuta cada vez que se alcanza el tiempo establecido
---

```python
import rclpy
from rclpy.node import Node

class MyFirstPublisher(Node):
    def __init__(self) -> None:
        super().__init__('my_first_publisher')
        # Create Publishers
        # Create Subscribers
        # Initialize attributes
        self.counter = 0
        # Create timers
        self.timer = self.create_timer(
	        1.0,self.timer_callback)
    # Create callback methods (subscribers and timers)
    def timer_callback(self):
	    self.counter = self.counter + 1
```
---

## Agregar Publishers
Para crear un publisher se requieren de dos partes:
- La variable que contiene el tipo de mensaje y a que topic se va a publicar
- El call para hacer el publish
---

```python
import rclpy
from rclpy.node import Node
from example_interfaces.msg import String

class MyFirstPublisher(Node):
    def __init__(self) -> None:
        super().__init__('my_first_publisher')
        # Create Publishers
        self.example_publisher = self.create_publisher(
	        String,"example_topic",10)
        # Create Subscribers
        # Initialize attributes
        self.counter = 0
        # Create timers
        self.timer = self.create_timer(
	        1.0,self.timer_callback)
    # Create callback methods (subscribers and timers)
    def timer_callback(self):
	    msg = String()
	    msg.data = "Hello World" + str(self.counter)
	    self.example_publisher.publish(msg)
	    self.counter = self.counter + 1
```
---
## Hacer el build del nodo
``` bash
cd
cd ros2_ws
colcon build --packages-select ros2_ws --symlink-install
cd
source .bashrc
```
---
## Correr el nodo
``` bash
ros2 run ros2_pkg MyFirstPublisher
```
Para confirmar que se haya creado el topic se puede hacer
``` bash
ros2 topic list
```
Para ver que está publicando se puede hacer echo
``` bash
ros2 topic echo /example_topic
```
---
![[topic list y topic echo.png]]

---
También se puede ver en rqt_graph
``` bash
rqt_graph
```
![[rqt_graph my first publisher.png|500]]

---
## Crear ejemplo de Nodo Subscriber
Ahora se seguirá el mismo procedimiento para crear un nodo subscriber
```bash
cd ~/ros2_ws/ros2_pkg/src/ros2_pkg/ros2_pkg
touch my_first_subscriber.py
chmod +x my_first_subscriber.py
```
---
### Copiar código de template al nuevo nodo y editar NodeName y node_name
``` python
import rclpy
from rclpy.node import Node

class MyFirstSubscriber(Node):
    def __init__(self) -> None:
        super().__init__('my_first_subscriber')
        # Create Publishers
        # Create Subscribers
        # Initialize attributes
        # Create timers
    # Create callback methods (subscribers and timers)
```
---
```python
def main(args=None) -> None:
    rclpy.init(args=args)
    my_first_subscriber = MyFirstSubscriber()
    rclpy.spin(my_first_subscriber)
    my_first_subscriber.destroy_node()
    rclpy.shutdown()
if __name__=='__main__':
    try:
        main()
    except Exception as e:
        print(e)
```
---
## Agregar ejecutable al setup.py
``` python
entry_points = {
	'console_scripts': [
			"MyFirstPublisher = ros2_pkg.my_first_publisher:main",
			"MyFirstSubscriber = ros2_pkg.my_first_subscriber:main"
		],
}
```
---
## Agregar Subscriber
Para crear un subscriber se requiere de dos partes:
- La variable que está escuchando al topic
- El callback que se ejecuta cada vez que se recibe un mensaje
---
Asegurarse que el tipo de msg y el topic sean los mismos que los del publisher!!
``` python
import rclpy
from rclpy.node import Node
from example_interfaces.msg import String

class MyFirstSubscriber(Node):
    def __init__(self) -> None:
        super().__init__('my_first_subscriber')
        # Create Publishers
        # Create Subscribers
        self.example_subscriber = self.create_subscription(
	        String,"example_topic",self.subscriber_callback,10)
        # Initialize attributes
        # Create timers
    # Create callback methods (subscribers and timers)
    def self.subscriber_callback(self,msg):
	    msg_received = msg.data
	    self.get_logger().info("Message received: " + msg_received)
```  
---
## Hacer el build del nodo
``` bash
cd
cd ros2_ws
colcon build --packages-select ros2_ws --symlink-install
cd
source .bashrc
```
---
## Correr publisher y subscriber
Correr el publisher
``` bash
ros2 run ros2_pkg MyFirstPublisher
```
Correr el subscriber
``` bash
ros2 run ros2_pkg MyFirstSubscriber
```
---
![[Publisher y subscriber.png]]
---
Para ver la interaccion entre ambos se puede ver rqt_graph
``` bash
rqt_graph
```
![[rqt_graph publisher y subscriber.png|500]]

---
## Crear publishers y subscribers en un mismo nodo
Ahora vamos a editar un poco el subscriber para que cada vez que reciba un mensaje, publique a un topic diferente el resultado de 2*n* msgs que haya recibido
Agregamos: 
- Int64 de example_interfaces
- Creamos un counter 
- Creamos un publisher
---
``` python
import rclpy
from rclpy.node import Node
from example_interfaces.msg import String, Int64

class MyFirstSubscriber(Node):
    def __init__(self) -> None:
        super().__init__('my_first_subscriber')
        # Create Publishers
        self.publisher_2n = self.create_publisher(
	        Int64,"multiplier_topic",10)
        # Create Subscribers
        self.example_subscriber = self.create_subscription(
	        String,"example_topic",self.subscriber_callback,10)
        # Initialize attributes
        self.counter = 0
        # Create timers
    # Create callback methods (subscribers and timers)
    def self.subscriber_callback(self,msg):
	    msg_received = msg.data
	    self.get_logger().info("Message received: " + msg_received)
	    new_msg = Int64()
	    new_msg.data = 2*self.counter
	    self.publisher_2n.publish(new_msg)
	    self.counter = self.counter + 1
```  
---
Como al buildear usamos *--symlink-install* automaticamente se actualiza el nodo
De nuevo corremos ambos nodos

Correr el publisher
``` bash
ros2 run ros2_pkg MyFirstPublisher
```
Correr el subscriber
``` bash
ros2 run ros2_pkg MyFirstSubscriber
```
---
Podemos hacer topic list y deben aparecer los 2 topics
``` bash
ros2 run topic list
```
Tambien podemos hacer echo al nuevo topic
``` bash
ros2 run topic echo /multiplier_topic
```
Finalmente podemos revisar rqt_graph
Correr el publisher
``` bash
rqt_graph
```
---
![[rqt_graph modified subscriber.png]]
---
### Ejemplo práctico

![[ejemplo_taller.png|500]]