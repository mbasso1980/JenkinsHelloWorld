pipeline {
    agent any 
    stages {
        stage('Static Code Scan') { 
            steps {
                echo "Static Code Scan stage"
                sh "COMMIT=`git rev-parse HEAD`"
                sh "echo $COMMIT"
            }
        }
        stage('Build') { 
            steps {
                echo "Build stage"
                sh "javac HelloWorld.java"
                archiveArtifacts artifacts: '*.class', fingerprint: true
            }
        }
        stage('Test') { 
            steps {
                echo "Test stage"
            }
        }
        stage('CM Approval') { 
            steps {
                input ("CM Approved?")
                echo "CM Approval"
            }
        }
        stage('Deploy') { 
            steps {
                echo "Deploy stage"
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
