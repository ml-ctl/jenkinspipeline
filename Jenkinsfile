pipeline {
    /* A Declarative Pipeline */
    agent any

    stages{
        stage('Build'){
            steps {
                echo 'Building...'
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }
    }
}