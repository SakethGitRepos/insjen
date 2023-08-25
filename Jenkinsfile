pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    docker.image('docker:latest').inside {
                        sh "docker build -t ngximg -f Dockerfile."
                    }
                }
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
