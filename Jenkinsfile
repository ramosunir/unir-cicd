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
                mail bcc: '', body: 'Hola, Esta es una notificacion de una ejecucion exitosa del proyecto en el jenkins pipeline.', cc: '', from: '', replyTo: '', subject: 'Notificacion de JenkinsPipeline', to: 'joel2064@gmail.com'
            }
        }
    }
    post {
        always {
            junit 'results/*_result.xml'
            cleanWs()
        }
    }
}