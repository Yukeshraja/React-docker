def CONTAINER_NAME="react"
def CONTAINER_TAG="latest"
def DOCKER_HUB_USER="yukesh"
def HTTP_PORT="8090"

node {

    stage('Initialize'){
        def dockerHome = tool 'myDocker'
    }

    stage('Checkout') {
        checkout scm
    }

    stage("Image Prune"){
        imagePrune(CONTAINER_NAME)
    }

    stage('Image Build'){
        imageBuild(CONTAINER_NAME, CONTAINER_TAG)
    }

    stage('Push to Docker Registry'){
       withCredentials([usernamePassword(credentialsId: 'dockerHubAccount', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
            pushToImage(CONTAINER_NAME, CONTAINER_TAG, USERNAME, PASSWORD)
        }
    }

    stage('Run App'){
        runApp(CONTAINER_NAME, CONTAINER_TAG, DOCKER_HUB_USER, HTTP_PORT)
    }

}

def imagePrune(containerName){
    try {
        sh "sudo docker image prune -f"
        sh "sudo docker stop $containerName"
    } catch(error){}
}

def imageBuild(containerName, tag){
    sh "sudo docker build -t $containerName:$tag  -t $containerName --pull --no-cache ."
    echo "Image build complete"
}

def pushToImage(containerName, tag, dockerUser, dockerPassword){
    sh "sudo docker login -u $yukesh -p $Yukesh@2991"
    sh "sudo docker tag $containerName:$tag $yukesh/$containerName:$tag"
    sh "sudo docker push $yukesh/$containerName:$tag"
    echo "Image push complete"
}

def runApp(containerName, tag, dockerHubUser, httpPort){
    sh "sudo docker pull $dockerHubUser/$containerName"
    sh "sudo docker run -d --rm -p $httpPort:$httpPort --name $containerName $dockerHubUser/$containerName:$tag"
    echo "Application started on port: ${httpPort} (http)"
}
