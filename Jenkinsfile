pipeline {
    agent any
    stages {
        stage('Clone Code') {
            steps {
                // Replace with your GitHub repository URL
                git branch: 'main', url: 'https://github.com/ishan014/Jenkins-Driven-CI-CD-Pipeline-for-Flask-MySQL-App.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t flask-app:latest .'
            }
        }
        stage('Deploy with Docker Compose') {
            steps {
                // Stop existing containers if they are running
                bat 'docker compose down || true'
                // Start the application, rebuilding the flask image
                bat 'docker compose up -d --build'
            }
        }
    }
}
