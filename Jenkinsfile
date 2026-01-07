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
        stage('Uruchomienie kontenera') {
            steps {
                // Czyścimy stary kontener, jeśli istnieje
                sh 'docker rm -f moja-apka-run || true'
                // Odpalamy nowy na porcie 8081
                sh 'docker run -d --name moja-apka-run -p 8081:80 moja-apka-devops'
            }
        }
    }
}
