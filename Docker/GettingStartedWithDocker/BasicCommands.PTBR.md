# Comandos básicos 

- `docker run {name}`: Para executar a imagem

- `docker ps`: Containers que estão rodando

- `docker ps -a`: Containers que já executaram, mas já "morreram" algum momento.

- `-i`: Modo interativo
- `-t`: TTY - Basicamente para nós poder digitar coisas no terminal. Normalmente são usados junntos `-it`

Exemplo: `docker run -it --rm ubuntu bash`

- `--rm`: Todo processo de container que subir, na hora que ele "sair", você já remove automaticamente.
