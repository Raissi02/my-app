pipeline {
  agent any

  stages {
    stage('Build Docker Image') {
      steps {
        script {
          docker.build("raissi02/my-app:latest")
        }
      }
    }

    stage('Push to Docker Hub') {
      steps {
        script {
          docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            docker.image("raissi02/my-app:latest").push()
          }
        }
      }
    }

    stage('Deploy to Kubernetes') {
      steps {
        script {
          sh "kubectl apply -f kubernetes/deployment.yaml"
        }
      }
    }
  }

 
