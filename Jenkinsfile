pipeline {
    environment {
      COMMIT="Basso"
    }
    agent any
    parameters {
        choice(choices: ['N/A', 'QA1', 'QA2', 'QA3', 'TST1', 'TST2'], description: 'Select a Test Database to deploy to.', name: 'TEST_DB')
        choice(choices: ['N/A', 'devel1:/IW/CI/fmerger/', 'devel1:/IW/CI/test/', 'devel1:/IW/CI/pbatch/', 'titan1:/IW/CI/test/'], description: 'Select a Test Codetree to deploy to.', name: 'TEST_CT')    
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
