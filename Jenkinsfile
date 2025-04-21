pipeline {
    agent any
    environment {
        IMAGE_NAME = 'prac05q4'
        APP_PORT = '3000'
        IMAGE_PATH = 'D:\DevOps\prac05q3'
    }
    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/whoschetna/DO_Practical_5q3.git'
            }
        }
        stage('Build Docker Image') {
            steps {
                script {
                    dir("${IMAGE_PATH}") {
                        bat 'docker build -t prac05q4 .'
                    }
                }
            }
        }
        stage('Run Docker Container') {
            steps {
                script {
                    bat 'docker run -p 3001:3000 prac05q4'
                }
            }
        }
    }
    post {
        always {
            echo 'Cleaning up any dangling containers...'
            script {
                bat 'docker container prune -f'
            }
        }
    }
}
