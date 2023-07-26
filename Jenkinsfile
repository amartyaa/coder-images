pipeline {
  agent any
  stages{
    stage('base image build'){
      steps{
        sh "docker build . -t base -f $workspace/images/Dockerfile"
      }
    }
  }
}