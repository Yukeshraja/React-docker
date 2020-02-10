node{
   stage('SCM Checkout'){
       checkout scm
   }
   
   stage('Build Docker Image'){
     sh 'docker build -t yukesh/react .'
   }
   stage('Push Docker Image'){
     withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerhubpwd')]) {
        sh "docker login -u yukesh -p ${dockerhubpwd}"
     }
     sh 'docker push yukesh/react'
   }
   stage('Run Container on Dev Server'){
     def dockerRun = 'docker run -p 8080:8080 -d --name my-app kammana/my-app:2.0.0'
     sshagent(['dev-server']) {
       sh "ssh -o StrictHostKeyChecking=no ec2-user@172.31.18.198 ${dockerRun}"
     }
   }
}
