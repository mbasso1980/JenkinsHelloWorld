pipeline {
    environment {
      COMMIT="Basso"
    }
    agent any
    parameters {
        string(defaultValue: "TEST", description: 'What environment?', name: 'userFlag')
        choice(choices: ['US-EAST-1', 'US-WEST-2'], description: 'What AWS region?', name: 'region')
    }
    stages {
        stage('Static Code Scan') { 
            steps {
                echo "Static Code Scan stage"
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
            when{
                branch 'master'
            }
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
