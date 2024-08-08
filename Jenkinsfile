pipeline {
  
  agent {
    label 'master'
  }
  
  stages {
    stage('Image Prune') {
      steps {
        sh 'sudo docker image rm -f yukesh/react'
      }}
  
  stage('Build Docker Image'){
    steps {
     sh 'sudo docker build -t yukesh/react:latest .'
    }}
    
  stage('Push Registry'){
    steps {
     sh 'sudo docker login -u=yukesh -p=Yukesh@2991'
     sh 'sudo docker push yukesh/react:latest'
    }}  
    
    stage('Remove Container'){
    steps {
     sh 'sudo docker rm -f react'
    }}  
    
    stage('Dev-docker-deploy'){
    steps {
     sh 'sudo docker run --name=react -d -p 8800:5000  yukesh/react:latest'
    }}  
   
      
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
