pipeline {
  
  agent {
    label 'slave01'
  }
    stages {
    stage('Image Prune') {
      steps {
        sh 'sudo docker image rm -f yukesh/react'
      }
    }
  
  stage('Build Docker Image'){
    steps {
     sh 'sudo docker build -t yukesh/react:latest'
    } }
      
}
}
   /*
    
   
   
   
   
   stage('Push Docker Image'){
     withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
        sh "docker login -u yukesh -p ${dockerHubPwd}"
     }
      sh 'docker push yukesh/react'
   }
   
   stage('Run Container on Dev Server'){
     sh 'docker pull yukesh/react:latest'
     sh 'docker run -d -p 8000:5000 --name:react yukesh/react:latest'
   }
   
}

*/
