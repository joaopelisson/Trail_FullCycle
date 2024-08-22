### Network
O Docker possui uma rede interna que roda dentro dele, permitindo diversas funcionalidades, principalmente a comunicação entre containers.

É muito comum que containers precisem se comunicar entre si.

Por exemplo, imagine que você tenha um aplicativo rodando em Laravel e um banco de dados MySQL em outro container. Ambos precisam se comunicar, mas não é ideal colocá-los no mesmo container.

Para que a aplicação Laravel se comunique com o MySQL, ambos precisam estar na mesma rede.

Quando falamos de rede no Docker, é importante entender que existem diferentes tipos de redes, especialmente quando o próprio Docker precisa se conectar à rede do seu computador.

---

🛜 Tipos de network:
- **Bridge**  
  Quando você cria uma network no Docker sem especificar o tipo, você está criando uma network do tipo bridge. Normalmente, usamos essa rede para permitir a comunicação entre containers.

  **Exemplo de caso de uso:**  
  Imagine que você tenha um ambiente de desenvolvimento onde vários containers precisam se comunicar, como um container rodando uma aplicação web e outro rodando um banco de dados. Usando uma network do tipo bridge, esses containers podem se comunicar facilmente, permitindo que a aplicação acesse o banco de dados.

- **Host**  
  Esse tipo de network é bastante importante, pois ele mescla a network do Docker com a network do host do Docker. Por exemplo, se você estiver rodando uma aplicação PHP na porta 80 da sua máquina e criar uma network do tipo host, ao subir um container nessa mesma network, o container poderá acessar diretamente a máquina host (sua máquina). Assim, sua máquina pode acessar uma porta diretamente no container sem a necessidade de expor a porta.

  **Exemplo de caso de uso:**  
  Imagine que você esteja desenvolvendo uma aplicação que precisa acessar diretamente os serviços rodando na máquina host, como um servidor de banco de dados local. Usando uma network do tipo host, o container pode se comunicar diretamente com esses serviços sem a necessidade de configuração adicional de portas.

- **Overlay**  
  Esse tipo de network é útil quando você tem vários containers em máquinas diferentes e precisa que eles se comuniquem como se estivessem na mesma rede. Um caso de uso comum é o Docker Swarm, que cria um cluster de vários Docker hosts para escalar sua aplicação. Para que containers em diferentes máquinas possam se comunicar, eles precisam estar em uma network do tipo overlay.

  **Exemplo de caso de uso:**  
  Imagine que você tenha uma aplicação web de grande escala que precisa ser altamente disponível e escalável. Você pode usar o Docker Swarm para criar um cluster de máquinas (nós) que executam múltiplos containers da sua aplicação. Com a network do tipo overlay, os containers podem se comunicar entre si, independentemente de estarem em máquinas diferentes. Isso permite que você distribua a carga de trabalho de forma eficiente e mantenha a comunicação entre os serviços, como um serviço de frontend se comunicando com um serviço de backend ou um banco de dados, mesmo que estejam em nós diferentes do cluster.

- **Macvlan**  
  Esse tipo de network permite que você atribua um endereço MAC a cada container, fazendo com que eles apareçam como dispositivos físicos distintos na rede. Isso é útil quando você precisa que os containers se comportem como se fossem máquinas físicas na rede, permitindo uma integração mais direta com a infraestrutura de rede existente.

  **Exemplo de caso de uso:**  
  Imagine que você está migrando uma aplicação legada que depende de endereços MAC específicos para controle de acesso ou licenciamento. Usando uma network do tipo macvlan, você pode atribuir endereços MAC específicos aos containers, permitindo que a aplicação funcione corretamente sem modificações significativas.

- **None**  
  Quando você cria um container com a network do tipo none, ele não terá acesso a nenhuma rede. Isso significa que o container não poderá se comunicar com outros containers ou com a rede externa.

  **Exemplo de caso de uso:**  
  Imagine que você precise rodar um container que executa uma tarefa isolada e não precisa se comunicar com outros serviços ou acessar a internet, como um processo de processamento de dados que lê e escreve em volumes montados. Usando a network do tipo none, você garante que o container fique completamente isolado da rede.