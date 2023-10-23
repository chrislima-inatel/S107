pipeline {
    agent any

    stages {
        stage ('Build'){
            steps {
                echo "Building..."
                sh 'mvn --version'
                sh 'java --version'
                sh 'ls'
                sh 'pwd'
                sh '''
                    cd Aula-GitHub-Actions
                    mvn clean install
                   '''
            }
        }

        stage ('Test'){
            steps {
                echo 'Testing'
                sh '''
                    cd Aula-GitHub-Actions
                    mvn clean test site
                   '''
                   archiveArtifacts 'Aula-GitHub-Actions/target/site/'
            }

        }

        stage ('Notifications'){
            steps {
                echo 'Notifications'
                sh '''
                    cd scripts/
                    chmod 777 *
                    ./jenkins.sh
                   '''
            }

        }
    }
}