pipeline {
  agent  {
      label 'dind-agent'
    }
  stages{
    stage('base image build'){
      steps{
        sh "echo sivalakshmi"
        sh "docker build -f images/base/Dockerfile.ubuntu -t test/ubuntu ."
      }
    }
  }
}