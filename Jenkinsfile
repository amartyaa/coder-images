pipeline {
  agent any
  stages {
    stage('Kaniko Build & Push Image') {
      agent{
        label 'kaniko'
      }
      steps {
        container('kaniko') {
          script {
            sh '''
            /kaniko/executor --dockerfile images/base/Dockerfile.ubuntu 
                             
            '''
          }
        }
      }
    }
  }
}