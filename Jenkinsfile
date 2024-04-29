pipeline {
    agent any 
    
    parameters {
        string defaultValue: 'DEV', name: 'ENV'
    }
    
    triggers {
        pollSCM '* * * * *'
    }
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh '/home/gaurav/Devops/apache-maven-3.9.6/bin/mvn install'
            }
        }
        stage('Deployment') {
            steps {
                script {
                    if (env.ENV == 'QA') {
                        sh 'cp target/pipeline.war /home/gaurav/Devops/apache-tomcat-9.0.88/webapps'
                        echo "Deployment has been COMPLETED on QA!"
                    } else if (env.ENV == 'UAT') {
                        sh 'cp target/pipeline.war /home/gaurav/Devops/apache-tomcat-9.0.88/webapps'
                        echo "Deployment has been done on UAT!"
                    }
                }
                stage('slack') {
                    steps {
                        slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'Mintra12', color: 'good', message: 'Welcome to Grras in Devops with Swapnil Mahajan', notifyCommitters: true, teamDomain: 'DevOps-Grras-Projacts', tokenCredentialId: '665ad951-6c57-4472-aa0c-1c93a6450104'
                    }
                }
            }
        }
    }
}



