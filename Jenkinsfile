pipeline {
  agent { label 'linux' }
  options {
    buildDiscarder(logRotator(numToKeepStr: '5'))
  }
  environment {
    DOCKERHUB_CREDENTIALS = credentials('prashola-dockerhub')
  }
  stages {
    stage('Build') {
      steps {
        sh 'docker build -t prashola/demo1:latest .'
      }
    }
    stage('login') {
      steps {
        sh ''
      }
    }
    stage('Push') {
      steps {
        sh '''
          docker login -u $DOCKERHUB_CREDENTIALS_USR -p $DOCKERHUB_CREDENTIALS_PSW
          docker push rashola/demo1:latest .
          docker logout
        '''
      }
    }
  }
} 
