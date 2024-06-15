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
    }
    post {
        always {
            junit 'results/*_result.xml'
            cleanWs()
        }
    }
}