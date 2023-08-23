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
                        sh "docker build -t ngximg -f dockerfile."
                    }
                }
            }
        }

        stage('Deploy with Docker Compose') {
            steps {
                // Deploy using Docker Compose
                script {
                    dockerComposePath = "/home/ec2-user/insjen/dockercompose.yml"  // Update with the actual path
                    sh "docker-compose -f $dockerComposePath up -d"
                }
            }
        }
    }
}
