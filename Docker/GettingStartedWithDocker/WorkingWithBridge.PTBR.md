# Trabalhando com Redes no Docker

Para gerenciar redes no Docker, o comando principal que você deve conhecer é o `docker network`. Ele oferece várias opções para criar, listar, inspecionar e remover redes, permitindo que você configure e controle como seus containers se comunicam.

### Listando as Redes Disponíveis

Um bom ponto de partida é verificar as redes já configuradas no Docker. Para isso, utilize:

```bash
docker network ls
```

Esse comando exibe todas as redes disponíveis, mostrando quais estão prontas para uso. Um resultado típico pode ser:

```bash
NETWORK ID     NAME      DRIVER    SCOPE
a1f44ec5cd9d   bridge    bridge    local
4cf449d96503   host      host      local
4891632868g4   none      null      local
```

### Entendendo a Rede Padrão

Por padrão, quando você cria um container sem especificar uma rede, o Docker o conecta automaticamente à rede `bridge`. Essa é a rede padrão, usada na maioria dos casos.

Para visualizar os detalhes da rede `bridge`, você pode usar o comando:

```bash
docker network inspect bridge
```

### Criando Sua Própria Rede

Se precisar de uma rede personalizada, você pode criá-la com o comando:

```bash
docker network create --driver bridge minharede
```

Após criar a rede, execute `docker network ls` novamente, e verá algo como:

```bash
NETWORK ID     NAME        DRIVER    SCOPE
...
4255db102e41   minharede   bridge    local
...
```

Sua nova rede `minharede` está agora pronta para uso.

### Conectando Containers à Rede

Além de criar redes, você pode conectar um container existente a uma rede específica. Para isso, use:

```bash
docker network connect minharede nomeDoContainer
```

Agora, se você rodar:

```bash
docker network inspect minharede
```

Você verá mais detalhes sobre a conexão do container com a rede `minharede`, permitindo que você gerencie melhor a comunicação entre seus containers.
