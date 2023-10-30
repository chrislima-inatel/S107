[![Java CI with Maven](https://github.com/chrislima-inatel/S107/actions/workflows/comprasCI.yml/badge.svg)](https://github.com/chrislima-inatel/S107/actions/workflows/comprasCI.yml)

# S107 - Gerência de Configuração e Evolução de Software
- Repositório da disciplina Gerência de Configuração e Evolução de Software - S107. 
- Instituto Nacional de Telecomunicações - Inatel. 
- Curso: Engenharia de Software.
- Prof. Christopher Lima



## Comandos úteis Docker

1. Verificar a versão do docker:

```
docker --version
```

2. Listar containers docker rodando atualmente:

```
docker ps
```

3. Listar imagens docker na máquina:

```
docker image ls
```

4. Download de uma imagem do docker hub:

```
docker pull nome_da_imagem
```

5. Construir uma imagem docker com um dockerfile:

```
docker build --tag="tag_para_imagem" <diretorio_onde_se_encontra_o_dockerfile>
```

6. Executar o container utilizando docker-compose

```
docker-compose -f <arquivo_docker_compose> up
```

6. Parar o container utilizando docker-compose

```
docker-compose -f <arquivo_docker_compose> down
```


## Dockerfile

É possível ter muitas necessidades específicas para criação de uma aplicação. Nesse caso, utilizamos uma "receita de bolo" que especifica todas essas necessidades.
Essa receita é chamada de Dockerfile. Tudo que precisamos para criar o nosso container específico, se encontra nesse arquivo.

## Comandos dockerfile

1. Dockerfile é um arquivo que deve ser versionado
2. FROM: Define nossa imagem docker base.
3. ENV: define variáveis de ambiente.
4. USER: define o nível de usuário para executar alguma função.
5. RUN: executa alguma comando no container

Para mais comandos e explicações: https://docs.docker.com/engine/reference/builder/


## Como enviar uma imagem para o dockerhub e compartilhar?

Utilize o tutorial do docker: https://docs.docker.com/get-started/04_sharing_app/

## Jenkinsfile

Jenkinsfile é um arquivo que substitui a criação de jobs na interface gráfica do Jenkins. É a maneira mais recomendada para criar Pipelines no Jenkins. É possível colocar o arquivo na raiz de um repositório (Jenkinsfile) que possibilita a criação de um Pipeline com código (Pipeline como código - conceito de infraestrutura como código). Essa técnica nos permite versionar e controlar o fluxo.


Documentação oficial: https://www.jenkins.io/doc/book/pipeline/jenkinsfile/

## docker-compose

Iniciar containers individuais pela linha comando pode se tornar uma tarefa complicada. Imagina ter que subir 10 containers com aplicações diferentes, que se comunicam. Imagina fazer esse processo para diversos "clientes"? A complexidade aumenta muito rápido e a quantidade de tarefa manual exigida se torna um risco grande.
Por isso, podemos utilizar o docker-compose para automatizar ainda mais o processo e conseguir gerenciar/orquestrar o processo de executar/desligar containers.

No arquivo do compose descrevemos a infraestrutura como código e como ela vai se comportar ao ser iniciado. Este aquivo nada mais é que um mapa dos comandos que precisariamos executar para executar os containers. Nesse repositório, temos o arquivo: docker-compose-jenkins.yaml:

1. version: Versão do docker-compose utilizada
2. services: Lista de containers que podem rodar. Reparar a identação. Logo abaixo do services precisamos especificar o nome do containers
3. image: Imagem da qual o container será inicializado
4. ports: Mapeamento de portas utilizados.
5. environment: Lista de variáveis de ambiente que aquele container utilizará.
6. volumes: Usado para mapear um volume de acesso a dados. Utilizado para realizar persistência de dados. Esse comando mapeia dados do container para dentro da máquina que está rodando o docker.

Documentação oficial: https://docs.docker.com/compose/
