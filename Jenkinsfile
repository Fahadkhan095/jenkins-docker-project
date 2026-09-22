pipeline {
    agent any

    environment {
        DOCKER_PATH = 'C:\\Users\\fahad\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin'
    }

    stages {

        stage('Checkout') {
            steps {
                echo 'Code checked out from GitHub'
            }
        }

        stage('Check Docker') {
            steps {
                bat '"%DOCKER_PATH%\\docker.exe" --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '"%DOCKER_PATH%\\docker.exe" build -t my-web-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                bat '"%DOCKER_PATH%\\docker.exe" stop my-web-container || exit /b 0'
                bat '"%DOCKER_PATH%\\docker.exe" rm my-web-container || exit /b 0'
                bat '"%DOCKER_PATH%\\docker.exe" run -d -p 8081:80 --name my-web-container my-web-app'
            }
        }
    }
}
