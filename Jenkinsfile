pipeline {
    agent any

    stages {
        stage('Example') {
            steps {
                echo '✅ This is a test pipeline from Jenkinsfile in GitHub!'
            }
        }
    }

    post {
        success {
            echo '🎉 Pipeline completed successfully!'
        }
        failure {
            echo '❌ Pipeline failed.'
        }
    }
}
