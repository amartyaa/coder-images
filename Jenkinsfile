pipeline {

  agent {
    kubernetes {
      yamlFile 'build.yaml'
    }
  }

  stages {
    stage('Kaniko Build & Push Image') {
      steps {
        container('kaniko') {
          script {
            sh '''
            /kaniko/executor --dockerfile `pwd`images/base/Dockerfile.ubuntu \
                             --context `pwd` \
                             --destination=docker-dev-local/ubuntu:${BUILD_NUMBER}
            '''
          }
        }
      }
    }