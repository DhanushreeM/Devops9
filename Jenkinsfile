pipeline {
    agent any

    environment {
        PATH = "C:\\Users\\admin\\AppData\\Local\\Programs\\DockerDesktop\\resources\\bin;${env.PATH}"
    }

    stages {

        stage('Check Docker') {
            steps {
                bat 'echo %PATH%'
                bat 'where docker'
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flaskapp .'
            }
        }

        stage('Remove Old Containers') {
            steps {
                bat 'docker rm -f dev-container || exit /b 0'
                bat 'docker rm -f test-container || exit /b 0'
            }
        }

        stage('Run Dev Container') {
            steps {
                bat 'docker run -d --name dev-container -p 5000:5000 flaskapp'
            }
        }

        stage('Run Test Container') {
            steps {
                bat 'docker run -d --name test-container -p 5001:5000 flaskapp'
            }
        }
    }
}
