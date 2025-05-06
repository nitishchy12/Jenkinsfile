pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/nitishchy12/YOUR-REPO.git'
        BRANCH = 'main'
    }

    stages {
        stage('Clone') {
            steps {
                echo "Cloning repository..."
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Docker Login') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'DOCKER_USER', passwordVariable: 'DOCKER_PASS')]) {
                    bat 'docker logout'
                    bat 'docker login -u %DOCKER_USER% -p %DOCKER_PASS%'
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t nitishchy12/sql:8 .'
            }
        }

        stage('Push Docker Image') {
            steps {
                bat 'docker push nitishchy12/sql:8'
            }
        }

        stage('Run Docker Container') {
            steps {
                bat 'docker run -d -p 8081:8081 nitishchy12/sql:8'
            }
        }

        stage('Test') {
            steps {
                echo 'Test step simulated...'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploy step simulated...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline failed!'
        }
    }
}
