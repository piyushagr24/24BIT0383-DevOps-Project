pipeline {
    agent any

    environment {
        IMAGE_NAME = "devops-assignment"
        CONTAINER_NAME = "devops-assignment"
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

        stage('Run Docker Container') {
            steps {
                bat """
                docker stop %CONTAINER_NAME% || ver > nul
                docker rm %CONTAINER_NAME% || ver > nul
                docker run -d -p 8081:80 --name %CONTAINER_NAME% %IMAGE_NAME%
                """
            }
        }
    }

    post {
        success {
            echo 'Docker deployment completed successfully.'
        }

        failure {
            echo 'Pipeline execution failed.'
        }
    }
}