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

       
    }

}