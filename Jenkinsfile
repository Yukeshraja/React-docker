

node{
   stage('SCM Checkout'){
       checkout scm
   }
   
   stage('Build Docker Image'){
      def CONTAINER_NAME="react"
      def CONTAINER_TAG="latest"
      def DOCKER_HUB_USER="yukesh"
     sh "docker build -t $container_Name:$CONTAINER_TAG  -t $container_Name --pull --no-cache ."
     echo "Image build complete"
   }
}
