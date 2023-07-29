pipeline {
  agent {
    kubernetes {
      yamlFile 'builder.yaml'
    }
  }
  stages {
    stage('Kaniko Build & Push Image') {
      steps {
        container('kaniko') {
          script {
            sh '''
            /kaniko/executor --dockerfile $workspace/images/base/Dockerfile.ubuntu \
                             --context `pwd` \
                             --destination=justmeandopensource/myweb:${BUILD_NUMBER}
            '''
          }
        }
      }
    }
  }
}
