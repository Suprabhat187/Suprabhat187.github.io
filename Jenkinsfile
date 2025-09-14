pipeline {
    agent any

    environment {
        IMAGE_NAME = 'portfolio'
    }

    stages {
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t ${IMAGE_NAME} /workspace/portfolio'
            }
        }
        stage('Run Portfolio Container') {
            steps {
                sh 'docker stop portfolio || true'
                sh 'docker rm portfolio || true'
                sh 'docker run -d -p 8082:80 --name portfolio ${IMAGE_NAME}'
            }
        }
    }
}
