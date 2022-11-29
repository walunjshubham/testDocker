pipeline {
    agent any
    tools{
    maven 'MAVEN'
    }
    stages {
        stage('Build') { 
            steps {
            sh 'mvn clean install'
            }
        }        
      
    }
    post{
    always{
    	junit(
    	allowEmptyResults:true,
    	testResults:'*test-reports.xml'
    	)
    }
    }

}
