pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/nitishchy12/Jenkinsfile'
        BRANCH = 'main'
        DOCKER_IMAGE = 'yourdockerhubusername/sql-custom'
        DOCKER_CREDENTIALS_ID = 'docker-hub-credentials'
    }

    stages {

        stage('Clone') {
            steps {
                echo "Cloning repository..."
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build SQL Image') {
            steps {
                script {
                    echo 'Building SQL Docker image...'
                    dockerImage = docker.build("${DOCKER_IMAGE}", "-f Dockerfile.mysql .")
                }
            }
        }

        stage('Push SQL Image') {
            steps {
                script {
                    echo 'Pushing image to Docker Hub...'
                    docker.withRegistry('https://index.docker.io/v1/', "${DOCKER_CREDENTIALS_ID}") {
                        dockerImage.push("latest")
                    }
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
                // Example: docker run command or docker-compose
            }
        }
    }

    post {
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
