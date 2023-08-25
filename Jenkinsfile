pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Deploy with Docker Compose') {
            steps {
                script {
                    sh "docker-compose -f dockercompose.yml up -d"
                }
            }
        }
    }
}
