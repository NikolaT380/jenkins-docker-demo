pipeline {
  agent any
  stages {
    stage('Clone repository') {
      steps {
        checkout scm
      }
    }

    stage('Build image') {
      steps {
        sh 'docker build -t nikolatane/nginx-hello:latest .'
      }
    }

    stage('Push image') {
      steps {
        sh 'echo $DOCKERHUB_CREDS_PSW | docker login -u $DOCKERHUB_CREDS_USR --password-stdin'
        sh 'docker push nikolatane/nginx-hello:latest'
      }
    }

  }
  environment {
    DOCKERHUB_CREDS = credentials('dockerhub-credentials-id')
  }
}