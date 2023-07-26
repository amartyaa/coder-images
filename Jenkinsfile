pipeline{
    agent {
        kubernetes {
            defaultContainer 'jnlp'
            yamlFile 'agentpod.yaml'
        }
    }
    stages{
        stage('clean up'){
            steps{
                deleteDir()
            }
        }
        stage('Cloning our Git') { 
            steps { 
                sh "git clone https://github.com/amartyaa/coder-images.git"
            }
        }
        stage ("test"){
            steps {
                container('docker') {
                    sh "docker build -t dockerimage images/base/Dockerfile.ubuntu"
                }
            }
        }
    }
}