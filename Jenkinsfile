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
                bat 'docker build -t employee-management:v1 .'
            }
        }

        stage('Stop Old Container') {
            steps {
                bat 'docker stop employee-management-container || exit 0'
                bat 'docker rm employee-management-container || exit 0'
            }
        }

        stage('Deploy Container') {
            steps {
                bat 'docker run -d --name employee-management-container -p 8082:80 employee-management:v1'
            }
        }
    }
}