pipeline {
    agent any
    stages {
        stage('Pobieranie kodu') {
            steps {
                checkout scm
            }
        }
        stage('Budowanie obrazu Docker') {
            steps {
                sh 'docker build -t moja-apka-devops .'
            }
        }
        stage('Wdrożenie na Kubernetes') {
            steps {
                sh 'docker rm -f moja-apka-run || true'
                sh 'kubectl apply -f deployment.yaml'
            }
        }
    }
}
