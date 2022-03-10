pipeline {
    agent any
    tools {
  jdk "Java"
}
    stages {
        stage('Checkout') {
            steps {
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'Prasad', url: 'https://github.com/prasadrao3040/maven-java-project.git']]])
            }
        } 
        stage('Build') {
            steps {
                sh 'mvn validate'
            }
        }
        stage('Clean') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('deploy') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'Tomcat', passwordVariable: 'password', usernameVariable: 'Tomcat')]) {
    // some block
}
            }
        }
        stage('Notification') {
            steps {
                slackSend channel: '#pipe-line-job-jenkins', color: 'yellow', message: 'This is pipe line job is successfully build', tokenCredentialId: 'slack'
            }
        }
    }
}
