pipeline {
    agent any

    environment {
        GIT_REPO = 'https://github.com/nitishchy12/Jenkinsfile'
        BRANCH = 'main'
    }

    stages {

        stage('Clone') {
            steps {
                echo "🔁 Cloning repository..."
                git branch: "${BRANCH}", url: "${GIT_REPO}"
            }
        }

        stage('Build') {
            steps {
                echo '🔧 Simulating Build step...'
            }
        }

        stage('Test') {
            steps {
                echo '🧪 Simulating Test step...'
            }
        }

        stage('Deploy') {
            steps {
                echo '🚀 Simulating Deploy step...'
            }
        }
    }

    post {
        success {
            echo '✅ Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed!'
        }
    }
}
