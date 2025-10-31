pipeline {
    agent any
    stages {
        stage('Build Docker Image') {
            steps {
                bat 'docker build -t registration:v1 .'
            }
        }
        stage('Push to Docker Hub') {
            steps {
                bat 'docker tag registration:v1 akshara4/registration:v1'
                sh 'docker push divyasri1282/registration:v1'
            }
        }
        stage('Deploy to Kubernetes') {
            steps {
                bat 'kubectl apply -f D:/week-2/deployment.yaml'
                sh 'kubectl apply -f D:/week-2/service.yaml'
            }
        
        }
        stage('Automated UI Test') {
            steps {
                bat 'D:/week-2/test_registration.py'
            }
        }
    }
}







