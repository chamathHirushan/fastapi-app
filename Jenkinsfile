pipeline {
    agent any

    stages {
        stage('Clone') {
            steps {
                git 'https://github.com/chamathHirushan/fastapi-app.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t fastapi-app .'
            }
        }

        stage('Stop & Remove Existing Container') {
            steps {
                sh '''
                docker stop fastapi-container || true
                docker rm fastapi-container || true
                '''
            }
        }

        stage('Run Docker Container') {
            steps {
                sh 'docker run -d --name fastapi-container -p 80:8000 fastapi-app'
            }
        }
    }
}
