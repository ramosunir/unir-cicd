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
                sh 'python3 --version'
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