pipeline {
  agent {
    kubernetes {
      defaultContainer ‘kaniko’ 
      yaml “”” 
      kind: Pod 
      spec: 
        serviceAccountName: jenkins-sa 
        containers: 
        — name: kaniko 
          image: gcr.io/kaniko-project/executor:debug-539ddefcae3fd6b411a95982a830d987f4214251 
          imagePullPolicy: Always 
          command: 
          — sleep 
          args: 
          — 9999999 “””
    }
  }

  stages {

    stage('Kaniko Build & Push Image') {
      steps {
        container('kaniko') {
          script {
            sh '''
            /kaniko/executor --dockerfile `pwd`/Dockerfile \
                             --context `pwd` \
                             --destination=justmeandopensource/myweb:${BUILD_NUMBER}
            '''
          }
        }
      }
    }

    stage('Deploy App to Kubernetes') {     
      steps {
        container('kubectl') {
          withCredentials([file(credentialsId: 'mykubeconfig', variable: 'KUBECONFIG')]) {
            sh 'sed -i "s/<TAG>/${BUILD_NUMBER}/" myweb.yaml'
            sh 'kubectl apply -f myweb.yaml'
          }
        }
      }
    }
  
  }
}
