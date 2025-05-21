pipeline {

    agent any

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
                   ./shell.sh
                   '''
            }
        }

        stage('Escrever na Collection do MongoDB') {
            steps {
                script {
                    def insertResult = sh (
                        script: '''
                            docker exec jenkins mongo --host mongodb --username root --password root --authenticationDatabase admin <<EOF
                            use teste_jenkins;
                            db.logs.insertOne({
                                mensagem: "Inserção feita pelo Jenkins em " + new Date(),
                                status: "ok",
                                etapa: "pipeline"
                            });
                            EOF
                        ''',
                        returnStatus: true
                    )

                    if (insertResult != 0) {
                        error("Falha ao escrever no MongoDB")
                    } else {
                        echo "Documento inserido com sucesso no MongoDB"
                    }
                }
            }
        }

    }
}