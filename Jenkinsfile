pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch : 'main', url: 'https://github.com/jagadeesh-chintha/jenkins-flask-ci-cd.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t myapp:latest .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                   docker stop myapp || true
                   docker rm myapp || true
                   docker run -d --name myapp -p 5000:5000 myapp:latest
                '''
            }
        }
    }
}
