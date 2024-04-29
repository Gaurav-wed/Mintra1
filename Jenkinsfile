pipeline {
    agent any 
    
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
                sh 'cp target/mintra1.war /home/gaurav/Devops/apache-tomcat-9.0.88/webapps'
            }
        }
    }
    
    stage('slack' ) {
        steps {
            slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'mintra12', color: 'good', message: 'welcome to Devops in Grras with Swapnil Mahajan', teamDomain: 'DevOps-Grras-Projacts', tokenCredentialId: '344d2c29-4eb6-47cc-a55a-76698798a410'
        }
    }
}
