pipeline {
  agent {
    kubernetes {
      yaml '''
apiVersion: v1
kind: Pod
metadata:
  name: pod
spec:
  containers: 
  - name: kaniko
    image: a6f034afb9b8246a4b069286109179cd-1585340972.eu-central-1.elb.amazonaws.com/docker-dev-local/kaniko-executor:debug
    command:
    - cat
    tty: true 
      '''
    }
  }
  stages {
    stage('Kaniko Build & Push Image') {
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