pipeline {
    agent any
    tools{
    maven 'MAVEN'
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
