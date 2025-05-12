pipeline {
    agent any

    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub-credentials') 
        DOCKERHUB_REPO = 'shaheerhaq/mlops-pipeline'
    }

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-pat', git branch: 'dev', url: 'https://github.com/Shaheer-Haq/Project_MLOps.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    docker.build("${DOCKERHUB_REPO}")
                }
            }
        }

        stage('Push to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-credentials') {
                        docker.image("${DOCKERHUB_REPO}").push('latest')
                    }
                }
            }
        }
    }
}
