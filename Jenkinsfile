pipeline {
    agent any
    tools{
    maven 'MAVEN'
    }
    stages {
        stage('Build') { 
            steps {
            checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'get', url: 'https://github.com/walunjshubham/testDocker.git']]])
            sh "mvn -Dmaven.test.failure.ignore=true clean package"
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
