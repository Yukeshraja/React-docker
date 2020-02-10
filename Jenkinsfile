node{
   stage('SCM Checkout'){
       checkout scm
   }
   
    stage ('Image Prune') {
    sh 'docker image rm -f yukesh/react'  
   }
   
   
   stage('Build Docker Image'){
     sh 'docker build -t yukesh/react .'
   } 
   
   stage('Push Docker Image'){
     withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
        sh "docker login -u yukesh -p ${dockerHubPwd}"
     }
      sh 'docker push yukesh/react'
   }
   
   stage('Run Container on Dev Server'){
     def dockerRun = 'docker run -p 8080:8080 -d --name react yukesh/react'
     sshagent(['dev-server']) {
       sh "ssh root@18.222.0.73"
     }
   }
   
}
