pipeline {
    agent any
    environment {
        DOCKERHUB_CREDS = credentials('dockerhub-credentials-id')
    }
    stages {
        stage('Clone repository') {
            steps {
                checkout scm
            }
        }
        stage('Build image') {
            steps {
                sh 'docker build -t ТВОЈ_DOCKER_USER/nginx-hello:latest .'
            }
        }
        stage('Push image') {
            steps {
                sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'
                sh 'docker push ТВОЈ_DOCKER_USER/nginx-hello:latest'
            }
        }
    }
}
