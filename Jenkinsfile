/*pipeline {
    agent any
	
	  tools
    {
       maven "MAVEN_HOME"
    }*/
pipeline {
	agent any
	
	  tools
    {
       maven "MAVEN_HOME"
    }
environment {
registry = "sreeteja07/samplewebapp"
registryCredential = 'dockerhub_id'
dockerImage = ''
}
 stages {
      stage('checkout') {
           steps {
             
                git branch: 'master', url: 'https://github.com/SreetejaK/CI-CD-using-Docker.git'
             
          }
        }
	 stage('Execute Maven') {
           steps {
             
                /*sh 'mvn package'*/
		   withDockerRegistry([ credentialsId: "dockerhub_id", url: "" ]){
		   sh 'mvn compile jib:build'
		   }
	   }
          }
        }
        

  /*stage('Docker Build and Tag') {
           steps {
              script {
		dockerImage = docker.build registry + ":$BUILD_NUMBER"
		}
                //sh 'docker build -t samplewebapp:latest .' 
                //sh 'docker tag samplewebapp suren67/samplewebapp:latest'
                //sh 'docker tag samplewebapp nikhilnidhi/samplewebapp:$BUILD_NUMBER'
               
          }
        }*/
     
  /*stage('Publish image to Docker Hub') {
          
            steps {
        withDockerRegistry([ credentialsId: "dockerhub_id", url: "" ]) {
          sh  'docker push sreeteja07/samplewebapp:latest'
            }*/
		    /*script {
docker.withRegistry( '', registryCredential ) {
dockerImage.push()
}
}
                  
          }
        }
     
     stage('Run Docker container on Jenkins Agent') {
             
            steps 
			{
				
                sh 'docker run -d -p 8005:8080 sreeteja07/samplewebapp'
 
            }
        }
 stage('Run Docker container on remote hosts') {
             
            steps {
                sh "docker -H ssh://jenkins@172.31.28.25 run -d -p 8003:8080 nikhilnidhi/samplewebapp"
 
            }
        }*/
 }
