pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh 'docker build -t jenkins-cicd-app .'
            }
        }

        stage('Test') {
            steps {
                sh 'docker run --rm jenkins-cicd-app cat /usr/share/nginx/html/index.html | grep "Jenkins CI/CD Pipeline"'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f jenkins-cicd-app || true'
                sh 'docker run -d --restart unless-stopped -p 8082:80 --name jenkins-cicd-app jenkins-cicd-app'
            }
        }
    }
}