pipeline {
    agent any

    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-app .'
            }
        }

        stage('Run Dev Container') {
            steps {
                bat 'docker run -d --name dev-container -p 5000:5000 flask-app'
            }
        }

        stage('Run Test Container') {
            steps {
                bat 'docker run -d --name test-container -p 5001:5000 flask-app'
            }
        }
    }
}
