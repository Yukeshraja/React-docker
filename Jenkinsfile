node{
   stage('SCM Checkout'){
       checkout scm
   }
   
   stage('Build Docker Image'){
     sh 'docker build -t yukesh/react .'
   } 
   
   stage ('Image Prune') {
    sh 'docker image rm -f yukesh/react'  
   }
   stage('Push Docker Image'){
     withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
        sh "docker login -u yukesh -p ${dockerHubPwd}"
     }
      sh 'docker push yukesh/react'
   }
   
}
