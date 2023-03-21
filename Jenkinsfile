pipeline {
  agent any
  stages {
    stage('Build Docker image') {
      when {
        branch 'main'
      }
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
      when {
        branch 'main'
      } 
      steps {
        script {
          sh 'docker run -dti --name mywebpage mywebpage'
        }
      }
    }
  }
}
