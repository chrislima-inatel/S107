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

         stage('API test'){

                    steps {
                        echo 'API test...'
                        sh '''
                           curl http://flask_api2:6000
                           '''
                    }
                }
    }
}