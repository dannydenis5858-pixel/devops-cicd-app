pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'git@github.com:dannydenis5858-pixel/devops-cicd-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo .'
            }
        }

        stage('Deploy') {
            steps {
                sh '''
                docker rm -f devops-demo || true
                docker run -d -p 8081:80 --name devops-demo devops-demo
                '''
            }
        }
    }
}
