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
                sh 'docker build -t devops-demo:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                docker stop devops-demo || true
                docker rm devops-demo || true
                docker run -d --name devops-demo -p 8081:80 devops-demo:latest
                '''
            }
        }
    }
}
