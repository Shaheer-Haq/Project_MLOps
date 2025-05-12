pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git credentialsId: 'github-pat', branch: 'dev', url: 'https://github.com/Shaheer-Haq/Project_MLOps.git'
            }
        }
    }
}
