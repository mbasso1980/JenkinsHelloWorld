pipeline {
    environment {
      COMMIT="Basso"
    }
    agent any
    parameters {
        choice(choices: ['PBatch_001_04172020_CD45gYt', 'PBatch_002_04172020_VB5gYt2', 'PBatch_003_04172020_SDffgdt'], description: 'Select an Artifact to deploy.', name: 'TEST_ART')
        choice(choices: ['N/A', 'QA1', 'QA2', 'QA3', 'TST1', 'TST2'], description: 'Select a Test Database to deploy to.', name: 'TEST_DB')
        choice(choices: ['N/A', 'devel1:/IW/CI/fmerger/', 'devel1:/IW/CI/test/', 'devel1:/IW/CI/pbatch/', 'titan1:/IW/CI/test/'], description: 'Select a Test Codetree to deploy to.', name: 'TEST_CT')    
    }
    stages {
        stage('Static Code Scan') { 
            steps {
                echo "Static Code Scan stage"
                sh "echo $COMMIT"
                sh "echo ${params.TEST_ART}"
                sh "echo ${params.TEST_DB}"
                sh "echo ${params.TEST_CT}"
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
