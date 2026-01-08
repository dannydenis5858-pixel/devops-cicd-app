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
                sh '''
                docker build -t devops-demo:latest .
                '''
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                # Stop and remove existing container if it exists
                docker ps -q --filter "name=devops-demo" | xargs -r docker stop
                docker ps -aq --filter "name=devops-demo" | xargs -r docker rm

                # Run new container
                docker run -d --name devops-demo -p 8081:80 devops-demo:latest
                '''
            }
        }
    }

    post {

