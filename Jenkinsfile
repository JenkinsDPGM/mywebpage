pipeline {
  agent any
  stages {
    stage('Build Docker image') {
      steps {
        script {
          app = docker.build("mywebpage")
          app.inside {
            sh 'echo $(curl localhost:80)'
          }
        }
      }
    }
    stage('Deploy') {
      steps {
        script {
          sh 'docker run -dti --name mywebpage mywebpage'
        }
      }
    }
  }
}
