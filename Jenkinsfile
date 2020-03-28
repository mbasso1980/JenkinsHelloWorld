pipeline {
    agent any 
    stages {
        stage('Build') { 
            steps {
                echo "Build stage"
                sh "javac HelloWorld.java"
            }
        }
        stage('Test') { 
            steps {
                echo "Test stage"
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deploy stage"
            }
        }
        stage('Consolidate Results') { 
            steps {
                input ("Do you want to consolidate results?")
                echo "Consolidate Results"
            }
        }
        stage('Email Notification') { 
            steps {
                mail bcc: '', body: 'Sample Email Notification', cc: '', from: '', replyTo: '', subject: 'Sample Email Notification Subject', to: 'mbasso@rogers.com'
                echo "Email Notification"
            }
        }
    }
}
