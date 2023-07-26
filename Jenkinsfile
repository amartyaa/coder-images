pipeline {
  agent any
  stages{
    stage('base image build'){
      steps{
        sh "docker build -f images/base/Dockerfile.ubuntu -t test/ubuntu ."
      }
    }
  }
}