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
                sh 'mvn sonar:sonar'
                }
            }
        }
}
}
