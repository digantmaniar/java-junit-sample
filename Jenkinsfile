pipeline {
	agent any
	tools {
        maven 'maven-3.6.3' 
        }
		
	stages {
	stage('Checkout Source') {
		steps {
				echo 'Check out the project'
				checkout scm  
		}
		}

    stage('Maven Building Artifacts'){
        steps {			
			bat "mvn clean package"
		}
	}	
    stage('Junit Test Results') {
		steps {			
			junit '**/target/surefire-reports/TEST-*.xml'
			archiveArtifacts 'target/*.jar'
		}
   }
    stage('Build Docker Image'){
     steps {		
			bat 'docker build -t test123 .'
		}
   }

     stage('Push Docker Image'){
		steps {
           withDockerRegistry([url: "https://310643530327.dkr.ecr.ap-southeast-1.amazonaws.com/test123",credentialsId: "ecr:ap-southeast-1:aws-credentials"]) {
           bat 'docker push 310643530327.dkr.ecr.ap-southeast-1.amazonaws.com/test123:latest'
               }
	    }
	}

}
}
