# Acessando Recursos do Docker Host a partir de um Container

Quando estamos executando um container e precisamos acessar uma porta ou recurso no host da máquina onde o Docker está rodando, podemos seguir os passos abaixo:

1. Primeiramente, iniciamos um container interativo:

   ```bash
   docker run --rm -it --name ubuntu ubuntu bash
   ```

2. Dentro do container, recomendo atualizar o sistema e instalar o `curl`:

   ```bash
   apt-get update
   apt-get install curl -y
   ```

3. Agora, suponha que o recurso que queremos acessar esteja disponível na porta 8000 do host (localhost:8000). Podemos fazer isso rodando o comando:

   ```bash
   curl http://host.docker.internal:8000
   ```

E pronto! Agora o nosso container consegue acessar recursos diretamente da máquina host.
