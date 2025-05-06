pipeline {
    agent any

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
                    bat 'docker build -t sql:8 .'
                }
            }
        }

        stage('Push SQL Image') {
            steps {
                script {
                     bat 'docker run -d -p "8081:8081" sql:8'
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

}
