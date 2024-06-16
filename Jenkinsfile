pipeline {
    agent any

    stages {
        stage('Source Stage') {
            steps {
                git 'https://github.com/ramosunir/unir-cicd.git'
            }
        }
        stage('Build') {
            steps {
                echo 'Building Stage'
                sh 'make build'
            }
        }
        stage('Unit tests') {
            steps {
                sh 'make test-unit'
                archiveArtifacts artifacts: '**/results/*.xml'
            }
        }
        stage('Notificacion correo') {
            steps {
                mail bcc: '', body: 'Hello, This is an email from jenkins pipeline.', cc: '', from: '', replyTo: '', subject:​​ 'EmailJenkinsPipeline', to: 'joel2064@gmail.com'
            }
        }
    }
    post {
        always {
            emailext body: 'A Test EMail', recipientProviders: [[$class: 'DevelopersRecipientProvider'], [$class: 'RequesterRecipientProvider']], subject: 'Test'
            junit 'results/*_result.xml'
            cleanWs()
        }
    }
}