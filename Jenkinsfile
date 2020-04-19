pipeline {
    agent any

    stages{
        stage('Init') {
            steps {
                echo "Testing..."
            }
        }

        stage('Build'){
            steps {
                echo "Building..."
            }
        }

        stage ('Deploy'){
            stage {
                echo "Code deployed..."
            }
        }
    }
}