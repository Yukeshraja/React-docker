def CONTAINER_NAME="react"
def CONTAINER_TAG="latest"
def DOCKER_HUB_USER="yukesh"

node{
   stage('SCM Checkout'){
       checkout scm
   }
   
   stage('Build Docker Image'){
     sh "docker build -t $containerName:$tag  -t $containerName --pull --no-cache ."
     echo "Image build complete"
   }
}
