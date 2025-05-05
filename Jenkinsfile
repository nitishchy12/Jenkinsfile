pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/nitishchy12/Jenkinsfile'
        BRANCH = 'main'
    }

    stages {

        stage('Clone') {
            steps {
                echo "Cloning repository..."
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                echo 'Build step simulated...'
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
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
