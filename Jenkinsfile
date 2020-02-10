pipeline {
	agent any
	
	stages {
		stage("Checkout") {
			steps {
				checkout scm
			}
		}
    }
	stages {
        	stage("Imagebuild")
            		steps {
               		     withCredentials([usernameColonPassword(credentialsId: 'dockerHubAccount', variable: 'Hubaccount')]) {
				     sh "Docker login -u ${dockerhubAccount} -p ${dockerhubAccount}"
} 
            }
    }
	
}
