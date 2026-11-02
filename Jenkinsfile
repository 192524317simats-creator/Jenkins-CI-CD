
pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building Docker image...'
                bat 'docker build -t jenkins-cicd-app .'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing application files...'
                bat 'if exist index.html (echo HTML file found) else (exit /b 1)'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
                bat 'docker rm -f jenkins-cicd-app'
                bat 'docker run -d -p 8082:80 --name jenkins-cicd-app jenkins-cicd-app'
            }
        }
    }
}
