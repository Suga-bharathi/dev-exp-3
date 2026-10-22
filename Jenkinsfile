
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Test') {
            steps {
                bat 'if exist index.html (exit /b 0) else (exit /b 1)'
                echo 'HTML file exists - Test passed'
            }
        }

        stage('Build') {
            steps {
                echo 'Preparing HTML application...'
                bat 'if not exist build mkdir build'
                bat 'copy /Y index.html build\\index.html'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying HTML application...'
                echo 'HTML application deployed successfully!'
            }
        }
    }

    post {
        success {
            echo 'HTML application deployed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
