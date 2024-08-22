### Network
Docker has an internal network that runs within it, allowing various functionalities, primarily the communication between containers.

It is very common for containers to need to communicate with each other.

For example, imagine you have an application running in Laravel and a MySQL database in another container. Both need to communicate, but it is not ideal to put them in the same container.

For the Laravel application to communicate with MySQL, both need to be on the same network.

When we talk about networking in Docker, it is important to understand that there are different types of networks, especially when Docker itself needs to connect to your computer's network.

---

🛜 Types of network:
- **Bridge**  
  When you create a network in Docker without specifying the type, you are creating a bridge network. Typically, we use this network to allow communication between containers.

  **Example use case:**  
  Imagine you have a development environment where multiple containers need to communicate, such as a container running a web application and another running a database. Using a bridge network, these containers can easily communicate, allowing the application to access the database.

- **Host**  
  This type of network is quite important because it merges the Docker network with the Docker host's network. For example, if you are running a PHP application on port 80 of your machine and create a host network, when you start a container on the same network, the container can directly access the host machine (your machine). Thus, your machine can access a port directly on the container without the need to expose the port.

  **Example use case:**  
  Imagine you are developing an application that needs to directly access services running on the host machine, such as a local database server. Using a host network, the container can directly communicate with these services without additional port configuration.

- **Overlay**  
  This type of network is useful when you have multiple containers on different machines and need them to communicate as if they were on the same network. A common use case is Docker Swarm, which creates a cluster of multiple Docker hosts to scale your application. For containers on different machines to communicate, they need to be on an overlay network.

  **Example use case:**  
  Imagine you have a large-scale web application that needs to be highly available and scalable. You can use Docker Swarm to create a cluster of machines (nodes) that run multiple containers of your application. With an overlay network, the containers can communicate with each other regardless of being on different machines. This allows you to efficiently distribute the workload and maintain communication between services, such as a frontend service communicating with a backend service or a database, even if they are on different nodes of the cluster.

- **Macvlan**  
  This type of network allows you to assign a MAC address to each container, making them appear as distinct physical devices on the network. This is useful when you need the containers to behave as if they were physical machines on the network, allowing more direct integration with the existing network infrastructure.

  **Example use case:**  
  Imagine you are migrating a legacy application that relies on specific MAC addresses for access control or licensing. Using a macvlan network, you can assign specific MAC addresses to the containers, allowing the application to function correctly without significant modifications.

- **None**  
  When you create a container with a none network, it will not have access to any network. This means the container will not be able to communicate with other containers or the external network.

  **Example use case:**  
  Imagine you need to run a container that performs an isolated task and does not need to communicate with other services or access the internet, such as a data processing task that reads and writes to mounted volumes. Using a none network, you ensure the container is completely isolated from the network.