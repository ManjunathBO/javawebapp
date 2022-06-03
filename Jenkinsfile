pipeline {
  agent {
      label 'maven' 
  }
	stages{
	  stage ('Build'){
	    steps{
		sh '''
			mvn clean install
			'''
		}
	  }

 stage('Code Quality Check (Sonarqube)')
        {
          steps
          {
             script
             {
               def sonarscanner = tool 'sonar_scanner'
               withSonarQubeEnv(credentialsId: ' b11bbd22f0abbb41ad066b254eccbcb700dba025') {
               
                    // some block
                    sh """
                    ${sonarscanner}/bin/sonar-scanner
                
                    """
                }
             }
          }
        }


  stage('Upload to Nexus') {
            steps {
                // Deploy to Nexus
               nexusPublisher nexusInstanceId: 'nexus', nexusRepositoryId: 'EED_Engg-Excellence-Devops-POC_maven_releases', packages: []
            }
        }
	}
}


