# Comandos básicos 

- `docker run {name}`: Para executar a imagem

- `docker ps`: Containers que estão rodando

- `docker ps -a`: Containers que já executaram, mas já "morreram" algum momento.

- `-i`: Modo interativo
- `-t`: TTY - Basicamente para nós poder digitar coisas no terminal. Normalmente são usados junntos `-it`

Exemplo: `docker run -it --rm ubuntu bash`

- `--rm`: Todo processo de container que subir, na hora que ele "sair", você já remove automaticamente.

Redirecionando a porte quando vou rodar um container, exemplo:
`docker run -p 8080:80 nginx`

Agora se eu abrir: `http://localhost:8080/`

<img src="./welcomeToNginx.png" />

Se caso o container "prenda" seu terminal após o `-run` você pode executar:

`docker run -d -p 80:80 nginx`

Pois quando rodamos `-d` (detached mode) estamos evitando que o terminal fique preso na execução

Caso precise remover um container, basta executar:
`docker rm {ContainerId Ou Name}` -> `docker rm 133601884b1b` ou `docker rm blissful_jepsen` 

ou remover e matar
`docker rm {name ou id} -f`