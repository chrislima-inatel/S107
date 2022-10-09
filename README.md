[![Java CI with Maven](https://github.com/chrislima-inatel/S107/actions/workflows/maven.yml/badge.svg)](https://github.com/chrislima-inatel/S107/actions/workflows/maven.yml)

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
docker images
```

4. Download de uma imagem do docker hub:

```
docker pull nome_da_imagem
```

5. Construir uma imagem docker com um dockerfile:

```
docker build --tag="tag_para_imagem" diretorio_dockerfile
```

## Dockerfile

É possível ter muitas necessidades específicas para criação de uma aplicação. Nesse caso, utilizamos uma "receita de bola" que especifica todas essas necessidades.
Essa receita é chamada de Dockerfile. Tudo que precisamos para criar o nosso container específico, se encontra nesse arquivo.

## Comandos dockerfile

1. Dockerfile é um arquivo que deve ser versionado
2. FROM: Define nossa imagem docker base.
3. ENV define variáveis de ambiente.
4. USER define o nível de usuário para executar alguma função.
5. RUN executa alguma comando no container

Para mais comandos e explicações: https://docs.docker.com/engine/reference/builder/
