pipeline{
    agent any
    stages{
        stage('Cloning our Git') { 
            steps { 
                git 'https://github.com/amartyaa/coder-images.git' 
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