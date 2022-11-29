pipeline {
    agent any
    tools{
    maven 'MAVEN'
    jdk 'jdk11'
    }
    stages {
        stage('Build') { 
            steps {
            sh '''
           		echo "PATH=${PATH}"
           		echo "M2_HOME=${M2_HOME}"
           		'''
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
