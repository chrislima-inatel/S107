# Define nossa imagem base
FROM jenkins/jenkins:lts-jdk11

# Cria uma variávei com o link para o maven
ARG MAVEN_URL=https://dlcdn.apache.org/maven/maven-3/3.9.5/binaries/apache-maven-3.9.5-bin.tar.gz

# Cria uma variável com a versão do maven
ARG MVN_VERSION=3.9.5

# Define nosso usuario dentro do container
USER root

# Executa comandos para instalar o maven
RUN apt-get update

RUN apt-get install -y wget

RUN wget --no-verbose -O /tmp/apache-maven-${MVN_VERSION}-bin.tar.gz $MAVEN_URL
RUN tar xzf /tmp/apache-maven-${MVN_VERSION}-bin.tar.gz -C /opt/
RUN ln -s /opt/apache-maven-${MVN_VERSION} /opt/maven
RUN ln -s /opt/maven/bin/mvn /usr/local/bin
RUN rm -f /tmp/apache-maven-${MVN_VERSION}-bin.tar.gz

# Define uma variavel de ambiente MAVEN_HOME que aponta para o local do maven
ENV MAVEN_HOME /opt/maven

# chown: comando linux que muda o dono de uma pasta. Nesse caso estamos dando permissao para o usuario jenkins
RUN chown -R jenkins:jenkins /opt/maven

# Instalando mailutils
RUN apt-get install -y mailutils

# Limpa arquivos baixados com apt-get
RUN apt-get clean

USER jenkins