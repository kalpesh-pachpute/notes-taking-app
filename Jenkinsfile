pipeline {
    agent any
    stages {
        stage ('checkout code') {
            steps {
                git branch:'main',
                url:'https://github.com/kalpesh-pachpute/notes-taking-app.git'
            }
        }
        stage ('verify Docker') {
            steps {
                bat 'docker --version'
                bat 'docker compose version'
            }
        }
        stage ('build container'){
            steps {
                bat 'docker compose build'
            }
        }
        stage ('deploy containers'){
            steps {
                bat 'docker compose down'
                bat 'docker compose up -d'
            }
        }
        stage ('verify deployment'){
            steps {
                bat 'docker compose ps'
                bat 'docker ps'
            }
        }
    }
    post {
        success {
            echo 'Deployment Successful'
        }
        failure {
            echo 'Deployment failed'
        }
    }
}