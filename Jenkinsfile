pipeline {
  agent {
    kubernetes {
      label 'example-kaniko-volumes'
      yaml """
kind: Pod
metadata:
  name: kaniko
spec:
  containers:
  - name: kaniko
    workingDir: /home/jenkins
    image: gcr.io/kaniko-project/executor:debug
    imagePullPolicy: Always
    command:
    - /busybox/cat
    tty: true
"""
    }
  }
  stages {
    stage('Build with Kaniko') {
      environment {
        PATH = "/busybox:/kaniko:$PATH"
      }
      steps {
        container(name: 'kaniko', shell: '/busybox/sh') {

          sh '''#!/busybox/sh
            /kaniko/executor --dockerfile `pwd`/images/base/Dockerfile.ubuntu  --context `pwd` --skip-tls-verify --insecure --insecure-pull --single-snapshot --destination=a6f034afb9b8246a4b069286109179cd-1585340972.eu-central-1.elb.amazonaws.com/docker-dev-local/test:1  --cleanup=true --build-arg USERNAME=siva --build-arg PASSWORD=Siva@VF12 --cache=true
          ''' 
        }
      }
    }
  }
}
