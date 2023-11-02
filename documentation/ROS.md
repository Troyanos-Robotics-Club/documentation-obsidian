# TLDR

**Robotic Operating System** (ROS2) es un framework de herramientas para programar robots. Puedes ver [[Presentacion Taller ROS]] para que te des una idea rápida de como funciona

[Video de introducción de ROS](https://vimeo.com/639236696)

# Requisitos

- [[Python]]
- [[Introduccion a Linux|Linux]]

# Instalación

- [[Virtual Machine ROS2 Setup]]

# ROS Vs ROS2

## **ROS**

- Developed in 2007
- Tailored for small-scale, research-focused projects
- Peer-to-peer network architecture
- Only supports TCPROS/UDPROS communication protocols
- Limited real-time capabilities
- Lacks support for modern DDS (Data Distribution Service)
- Not designed with security in mind
- Custom serialization

## **ROS2**

- Launched in 2017
- Suitable for large-scale, industrial and commercial applications
- Decentralized discovery mechanism and network architecture
- Supports a variety of DDS communication protocols
- Improved real-time support
- Built-in support for DDS, enabling better scalability and robustness
- Enhanced security features (authentication, encryption)
- Standardized serialization (CDR)

## **Why We Chose ROS2**

- **Scalability**: Adaptability to large-scale and complex systems.
- **Real-time Computing**: Predictable execution suitable for critical applications.
- **Robustness**: Improved reliability and fault tolerance with DDS.
- **Security**: Enhanced security model for safe and secure communication.
- **Modernity**: Compatible with the latest technologies and standards.>)

> [!danger] ROS 1 está en su final de vida
> Próximamente será descontinuado

# Use Cases

1. **Autonomous Vehicles:** ROS2's real-time capabilities and improved security are critical for the development and operation of self-driving cars, drones, and underwater vehicles.
1. **Industrial Automation:** Robotics arms, automated guided vehicles (AGVs), and other robotic systems in manufacturing and logistics can benefit from ROS2's improved communication and control features.
1. **Internet of Things (IoT):** ROS2 can facilitate the integration of robots with sensors and other IoT devices in smart homes, smart cities, and smart factories due to its support for diverse communication protocols.
1. **Healthcare Robotics:** In surgical robots, rehabilitation devices, and hospital logistics robots, ROS2's real-time processing and enhanced security ensure safe and reliable operations.
1. **Aerospace:** For drones and rovers used in exploration, mapping, and surveillance, ROS2 offers robustness and the ability to handle complex communication systems.
1. **Collaborative Robots (Cobots):** ROS2's features support better human-robot interaction, necessary for cobots working alongside humans in shared workspaces.
1. **Research and Education:** Academic institutions can use ROS2 for cutting-edge research in robotics, ensuring that students and researchers are working with industry-standard tools.
1. **Entertainment:** Theme parks and entertainment industries can employ ROS2 to control animatronics and interactive robots for enhanced audience experiences.
1. **Agriculture:** For precision agriculture, ROS2 can help manage fleets of agricultural robots used for planting, monitoring crops, and harvesting.
1. **Search and Rescue Missions:** ROS2's reliable communication system is ideal for coordinating multiple robots in challenging environments during search and rescue operations.
1. **Marine Robotics:** In underwater exploration and monitoring, ROS2's support for robust, distributed systems is invaluable for managing complex tasks and data collection.
1. **Service Robots:** For robots that operate in service industries, like those in hospitality or retail, ROS2's enhanced interaction capabilities and security features are crucial.
1. **Military and Defense:** ROS2 can be used to develop and deploy robots for surveillance, bomb disposal, and logistics support in defense applications.
1. **Space Exploration:** Space rovers and robotic assistants for astronauts can be developed using ROS2, taking advantage of its robustness and advanced communication capabilities.

# Resources

- [Master class de los Davids](https://docs.google.com/presentation/d/12MQvNZLskTw1K3FWdAOfohYAyWYEZ9h1VF7JYy8C03U/edit#slide=id.g1cbfaafe841_0_273)
- [Templates de ROS de nodos](https://github.com/ros2/examples)
