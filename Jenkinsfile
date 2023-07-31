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
    image: a6f034afb9b8246a4b069286109179cd-1585340972.eu-central-1.elb.amazonaws.com/docker-dev-virtual/kaniko-executor:debug
    env:
    - name: USERNAME
      value: siva
    - name: PASSWORD
      value: "Siva@VF12"
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
            sh '''`pwd` 
            executor --dockerfile images/base/Dockerfile.ubuntu --build-arg USERNAME=siva --build-arg PASSWORD=Siva@VF12 --cache=true"
                             
            '''
          }
        }
      }
    }
  }
}