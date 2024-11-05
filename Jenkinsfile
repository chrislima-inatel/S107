pipeline {

    agent any

    environment {
            MONGO_HOST = 'mongodb'
            MONGO_PORT = '27017'
            MONGO_DATABASE = 'my_database'
            MONGO_COLLECTION = 'my_collection'
    }


    stages {

        stage('Build'){

            steps {
                echo 'Building...'
                sh "mvn --version"
                sh "java --version"
                sh '''
                   cd Aula-GitHub-Actions
                   mvn clean install
                   cd ${WORKSPACE}
                   ls
                   '''
                   archiveArtifacts 'Aula-GitHub-Actions/target/'

            }

        }

        stage('Test'){

            steps {
                echo 'Testing...'
                sh '''
                   cd Aula-GitHub-Actions
                   mvn clean test site
                   '''
            }

        }

        stage('Notification'){

            steps {
                echo 'Notification...'
                sh '''
                   cd scripts
                   chmod 775 *
                   '''
            }

        }

        stage('Install MongoDB Client') {
            steps {
                // Instalação do cliente MongoDB a partir do repositório oficial
                sh '''
                apt-get update &&
                apt-get install -y gnupg &&
                wget -qO - https://www.mongodb.org/static/pgp/server-4.4.asc | apt-key add - &&
                echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu $(lsb_release -cs)/mongodb-org/4.4 multiverse" | tee /etc/apt/sources.list.d/mongodb-org-4.4.list &&
                apt-get update &&
                apt-get install -y mongodb-org-shell
                '''
            }
        }

        stage('Write to MongoDB') {

            steps {
                script {
                    // Comando para inserir um documento JSON no MongoDB

                    sh """
                    mongo ${MONGO_HOST}:${MONGO_PORT}/${MONGO_DATABASE} --eval '
                    db.${MONGO_COLLECTION}.insert({ name: "Jenkins", description: "Inserindo do pipeline" });
                    '
                    """
                }
            }
        }

    }

}