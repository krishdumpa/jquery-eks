pipeline {
  agent any
  stages {
    stage('Code checkout') {
      steps {
        git(url: 'git@github.com:krishdumpa/jquery-eks.git', branch: 'main')
      }
    }

    stage('login to ECR') {
      steps {
        sh 'aws ecr get-login-password --region us-east-2 | sudo docker login --username AWS --password-stdin 635677005881.dkr.ecr.us-east-2.amazonaws.com'
      }
    }

    stage('Build docker image') {
      steps {
        sh 'sudo docker build -t 635677005881.dkr.ecr.us-east-2.amazonaws.com/jquery:$BUILD_NUMBER .'
      }
    }

    stage('push dockerimage') {
      steps {
        sh 'sudo docker push 635677005881.dkr.ecr.us-east-2.amazonaws.com/jquery:$BUILD_NUMBER'
      }
    }

    stage('create Namespace') {
      steps {
        sh 'kubectl apply -f k8s/namespace.yml'
      }
    }

    stage('Deployment') {
      steps {
        sh 'kubectl apply -f k8s/deployment.yml'
      }
    }

    stage('Service') {
      steps {
        sh 'kubectl apply -f k8s/service.yml'
      }
    }

  }
}