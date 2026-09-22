pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t my-web-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat 'docker stop my-web-container || exit /b 0'
                bat 'docker rm my-web-container || exit /b 0'
                bat 'docker run -d -p 8081:80 --name my-web-container my-web-app'
            }
        }
    }
}