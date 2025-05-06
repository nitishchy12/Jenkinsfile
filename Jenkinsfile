pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/nitishchy12/Jenkinsfile'
        BRANCH = 'main'
        IMAGE_NAME = 'nitishchy12/sql:8'
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
                    bat "echo %DOCKER_PASS% | docker login -u %DOCKER_USER% --password-stdin"
                }
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat "docker build -t %IMAGE_NAME% ."
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    bat "docker push %IMAGE_NAME%"
                }
            }
        }

        stage('Run Docker Container') {
            steps {
                script {
                    bat "docker run -d -p 8081:8081 %IMAGE_NAME%"
                }
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
        success {
            echo 'Pipeline succeeded!'
        }
    }
}
