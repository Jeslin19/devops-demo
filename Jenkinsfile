pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Jeslin19/devops-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-demo .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker stop devops-container || true'
                sh 'docker rm devops-container || true'
                sh 'docker run -d -p 8081:80 --name devops-container devops-demo'
            }
        }
    }

    post {
        success {
            echo 'Deployment successful!'
        }

        failure {
            echo 'Deployment failed!'
        }
    }
}
