pipeline {
    agent any

    environment {
        BACKEND_IMAGE = "taskify-backend"     
        FRONTEND_IMAGE = "taskify-frontend"   
    }

    stages {

        stage('Checkout Code') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/ademchebbi77/Taskify.git'
            }
        }

        stage('Build Backend Image') {
            steps {
                dir('taskify-back') {
                    sh "docker build -t ${BACKEND_IMAGE} ."
                }
            }
        }

        stage('Build Frontend Image') {
            steps {
                dir('TaskifyFront') {
                    sh "docker build -t ${FRONTEND_IMAGE} ."
                }
            }
        }

        stage('Images Ready (Livrables)') {
            steps {
                sh 'docker images'
            }
        }
    }

    post {
        success {
            echo ' Pipeline succeeded. Docker images are ready.'
        }
        failure {
            echo ' Pipeline failed. Check logs above.'
        }
    }
}
