pipeline {
    /* A Declarative Pipeline */
    agent any

    tools {
        maven 'localMaven'
    }
    
    stages{
        stage('Build'){
            steps {
                echo 'Building...'
                sh 'mvn clean package2'
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