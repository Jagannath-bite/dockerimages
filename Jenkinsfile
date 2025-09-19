pipeline {
    agent any

    environment {
        DOCKER_IMAGE = "htmlimage"
    }

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/Jagannath-bite/dockerimages.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $DOCKER_IMAGE:latest .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f html-app || true
                docker run -d --name html-app -p 7070:80 $DOCKER_IMAGE:latest
                '''
            }
        }
    }
}
