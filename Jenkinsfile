pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Checkout the Git repository
                checkout scm
            }
        }
        
        stage('Build Docker Image') {
            steps {
                // Build the Docker image
                script {
                    docker.image('docker:latest').inside {
                        sh "docker build -t ngximg -f Dockerfile."
                    }
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                // Deploy using Docker Compose
                script {
                    sh "docker-compose -f dockercompose.yml up -d"
                }
            }
        }
    }
}
