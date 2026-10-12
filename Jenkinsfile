pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'
            }
        }
        stage('Build Docker Image') {
            steps {
                sh 'docker build -t java-app-image:latest .'
            }
        }
        stage('Run Docker Container') {
            steps {
                sh 'docker rm -f java-app-container || true'
                sh 'docker run -d --name java-app-container java-app-image:latest'
            }
        }
    }
}
