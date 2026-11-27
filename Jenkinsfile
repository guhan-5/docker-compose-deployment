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
                sh 'docker compose -p docker-compose-deployment build'
            }
        }

        stage('Deploy Application') {
            steps {
                sh 'docker compose -p docker-compose-deployment down || true'
                sh 'docker compose -p docker-compose-deployment up -d'
            }
        }

        stage('Verify Deployment') {
            steps {
                sh 'docker compose -p docker-compose-deployment ps'
            }
        }
    }
}
