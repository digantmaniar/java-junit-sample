pipeline {

		stage('Checkout Source') {
				echo 'Check out the project'
				checkout scm  
				
			}

    stage('Maven Building Artifacts')
    {
        def mvnHome = tool name: 'Maven-new', type: 'maven'
        def mvnCMD="${mvnHome}/bin/mvn"
        sh label: '', script: "${mvnCMD} clean package"
    }
    stage('Junit Test Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
      archiveArtifacts 'target/*.jar'
   }

}
