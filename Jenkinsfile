pipeline {
    agent any

    environment {
        IMAGE_NAME = "devops-assignment"
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Repository checked out successfully'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat "docker build -t %IMAGE_NAME% ."
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f deployment.yaml'
                bat 'kubectl apply -f service.yaml'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully to Kubernetes.'
        }

        failure {
            echo 'Pipeline execution failed.'
        }
    }
}