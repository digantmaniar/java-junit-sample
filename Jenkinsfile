pipeline {
	agent any
	tools {
        maven 'maven-3.6.3' 
        }
		
stages {
	stage('Checkout Source') {
				echo 'Check out the project'
				checkout scm  
		}

    stage('Maven Building Artifacts')
    {
        bat "mvn clean install"
    }
    stage('Junit Test Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }

}
}
