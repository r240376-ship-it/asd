
pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                checkout scm
                echo 'Code downloaded from GitHub'
            }
        }

        stage('Build') {
            steps {
                sh 'test -f index.html'
                sh 'docker build -t webapp-image .'
                echo 'Docker image created'
            }
        }

        stage('Deploy') {
            steps {
                sh 'docker rm -f webapp || true'
                sh 'docker run -d --name webapp -p 8081:80 webapp-image'
                echo 'Web application deployed'
            }
        }
    }
}
