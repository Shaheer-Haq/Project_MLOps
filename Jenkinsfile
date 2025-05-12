pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials') 
        DOCKERHUB_REPO = 'shaheerhaq/mlops-pipeline'
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-pat', branch: 'dev', url: 'https://github.com/Shaheer-Haq/Project_MLOps.git'
            }
        }

        stage('Pull Docker Image') {
            steps {
                script {
                    // Pull the Docker image from Docker Hub
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image("${DOCKERHUB_REPO}:latest").pull()
                    }
                }
            }
        }
    }
}
