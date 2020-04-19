pipeline {
    agent any

    parameters {
         string(name: 'tomcat_dev', defaultValue: '127.0.0.1', description: 'Staging Server')
         string(name: 'tomcat_prod', defaultValue: '18.188.104.201', description: 'Production Server')
    }

    triggers {
         pollSCM('* * * * *')
     }

    stages {
        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
            post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

        stage ('Deployments') {
            parallel {
                stage ('Deploy to Staging'){
                    steps {
                        sh "cp **/target/*.war /Users/DCHENG/Documents/Dev/apache-tomcat-9.0.34-staging/webapps"
                    }
                }

                stage ("Deploy to Production"){
                    steps {
                        sh "scp -i /Users/DCHENG/Dev/aws/security/cs-tomcat-work.pem **/target/*.war ec2-user@${params.tomcat_prod}:/root/apache-tomcat-9.0.34/webapps"
                    }
                }
            }
        }
    }
}