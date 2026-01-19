pipeline {
  agent any

  environment {
    IMAGE_NAME = "myfastapi:latest"
    CONTAINER_NAME = "myfastapi"
  }

  stages {
    stage('Checkout') {
      steps {
        checkout scm
      }
    }

    stage('Build Docker Image') {
      steps {
        sh '''
          docker build -t ${IMAGE_NAME} .
        '''
      }
    }

    stage('Run Container') {
      steps {
        sh '''
          docker rm -f ${CONTAINER_NAME} || true
          docker run -d --name ${CONTAINER_NAME} -p 8000:8000 ${IMAGE_NAME}
        '''
      }
    }
  }
}
