pipeline{
    agent any
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
            agent{ docker { image 'docker' } }
            steps{
                script{
                    sh "echo Amartya"
                }
            }
        }
    }
}