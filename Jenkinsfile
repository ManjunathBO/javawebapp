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

stage ('Code Quality'){
            steps {
                withSonarQubeEnv('SonarQube'){
                sh '''
			
		mvn sonar:sonar
		'''
  -Dsonar.projectKey=sonarqubekey 
  -Dsonar.host.url=http://13.52.182.221:9000 
  -Dsonar.login=e419ece308285ff449417b30285411d267537e78
                }
            }
        }
   }
}
