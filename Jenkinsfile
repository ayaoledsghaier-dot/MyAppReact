
pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                echo 'Getting project from GitHub'
                checkout scm
            }
        }

        stage('Check Docker') {
            steps {
                bat 'docker --version'
                bat 'docker compose version'
            }
        }

        stage('Build Docker Images') {
            steps {
                bat 'docker compose build'
            }
        }

        stage('Deploy Application') {
            steps {
                bat 'docker compose up -d'
            }
        }

        stage('Check Containers') {
            steps {
                bat 'docker compose ps'
            }
        }
    }

    post {
        success {
            echo 'Application deployed successfully!'
        }

        failure {
            echo 'Pipeline failed. Check the logs.'
            bat 'docker compose logs'
        }
    }
}
