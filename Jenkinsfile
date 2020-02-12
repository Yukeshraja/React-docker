pipeline {
  environment {
    registry = "yukesh/react"
    registryCredential = ‘dockerhub’
}
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
     sh 'dockerImage = docker.build registry + ":$BUILD_NUMBER"'
    } }
      
    stage('Push Docker Image'){
     sh 'docker.withRegistry( '', registryCredential ) {
            dockerImage.push()'
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
