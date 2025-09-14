pipeline {
    agent any

    environment {
        IMAGE_NAME = 'portfolio'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                echo "Building Docker image from workspace..."
                sh 'docker build -t ${IMAGE_NAME} ${WORKSPACE}'
            }
        }
        stage('Run Portfolio Container') {
            steps {
                echo "Stopping old container if exists..."
                sh 'docker stop portfolio || true'
                sh 'docker rm portfolio || true'
                echo "Running new container..."
                sh 'docker run -d -p 8082:80 --name portfolio ${IMAGE_NAME}'
            }
        }
    }
}
