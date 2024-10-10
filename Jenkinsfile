pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Mathissalvador/DevSecOps-TP01.git'
            }
        }
        stage('Build') {
            steps {
                sh 'docker build -t my-devsecops-app .'
            }
        }
        stage('Test') {
            steps {
                sh 'docker run -d -p 8080:8080 my-devsecops-app'
                sh 'curl http://localhost:8080'
            }
        }
        stage('Security Scan') {
            steps {
                sh 'trivy image my-devsecops-app'
            }
        }
        stage('Clean Up') {
            steps {
                sh 'docker stop $(docker ps -q)'
            }
        }
    }
}
