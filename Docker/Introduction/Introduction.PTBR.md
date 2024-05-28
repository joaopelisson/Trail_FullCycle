# Introdução ao Docker 🐋

- O que são Containers

- Como funcionam os Containers

- Como o Docker funciona

- Principais comandos utilizando Docker

- Dockerfile

- Trabalhando com imagens Docker

---

### O que são Containers?

É um padrão de unidade de software que empacota código e suas depêndencias, para que a mesma seja executada rapidamente de forma confiável de um ambiente computacional para o outro

---

### Como funcionam os Containeres?


#### Primeiro ponto quando falamos de container são os processos e os `namespaces` que isolam esses processos, trabalhando no sistema operacional da seguinta forma:

| Namespaces                                                           |
|----------------------------------------------------------------------|
| &nbsp;Sistema operacional                                            |
| &nbsp;&nbsp;Processo pai Container 1                                 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Processo filho container 1 |
| &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;Processo filho container 2 |

uma vez que matamos o processo pai, todos processo filhos são mortos juntos

Ou seja, `namespaces` = Isola os Processos.

#### Cgroups

A ideia do CGroups é isolar os recursos computacionais desse processo, para não prejudicar os demais

Não adianta ter apenas o processos isolados, precisamos ter esse isolamento nos recursos também para não prejudicar os outros recursos da "nossa máquina"

`Cgroups` = Controla os recursos


### File System

A Ideia é a gente trabalhar com camadas (layers)

`File System` = OFS (Overlay File System)


#### Imagens

A Imagem é onde carrega a estrutura, o necessário que precisamos para funcionar.

Trabalhando com camadas de depências.

_Exemplo:_ `myAppImage:v1`

#### Dockerfile

Um arquivo declarativo aonde escrevemos como vai ser a imagem que vamos utilizar, ou seja, usamos para construir imagens!

```
FROM: ImageName
RUN: comandos ex: apt-get install
EXPOSE: 8000
```

Ou seja...

`myDockerFile` -> build -> `myImage`

O Docker file gera o `Build`, quando o build é gerado, uma nova imagem é gerada.


Outra forma de gerar imagens é:

`myImage` -> commit -> `myImage:v2`

Eu pego um container que esta rodando, escrevo na camada de `Write` e quando faço um commit, uma imagem é gerada


#### Aonde ficam as imagens?

Fica no `Image registry`

| IMAGE REGISTRY |
|----------------|
| IMAGE N        |
| IMAGE Y        |
| IMAGE X        |

Toda vez que eu gero uma nova imagem a partir do dockerfile, essa imageName esta vindo de um `image registry` (ou seja, esta fazendo um `pull`)

Porem, quando vou gerar o Build dessa imagem, eu posso fazer um `push`, uma vez que eu estou fazendo um `push`, eu estou jogando no meu `image registry`

---


### Como o Docker funciona?

<img src="./How docker works.png" alt="Como docker funciona" />
