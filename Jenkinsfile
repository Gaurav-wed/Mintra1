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
                sh 'cp target/pipeline.war /home/gaurav/Devops/apache-tomcat-9.0.88/webapps'
            }
        }
        
        stage('slack') {
            steps {
                slackSend baseUrl: 'https://hooks.slack.com/services/', channel: 'mintra', color: 'good', message: 'Welcome to Devops in GRRAS with Swapnil Mahajan', teamDomain: 'DevOps-Grras-Projacts', tokenCredentialId: 'c164738e-3163-49fb-9d07-71abf5d8f78a'
            }
        }
    }
}

