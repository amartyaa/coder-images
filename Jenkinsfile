pipeline {
  agent any
  stages{
    stage('base image build'){
      steps{
        sh "docker build -t base $wokrspace/images/base/Dockerfile.ubuntu"
      }
    }
  }
}