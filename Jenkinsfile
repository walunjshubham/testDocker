pipeline {
    agent any
    tools{
    maven 'MAVEN'
    }
    stages {
       stage('Build') { 
            steps {
            bat 'mvn clean install'
            }
        }        
    stage('Build image') { 
        steps{
        script{
        	sh 'docker build -t shubhamwalunj25/testdocker_2:latest .'
        	}
            }
        }
        stage('Push image to docker hub'){
        steps{
 			script{
        	withCredentials([string(credentialsId: 'dockerhubpwd', variable: 'dockerhubpwd')]) {
    		bat 'docker login -u shubhamwalunj25 -p ${dockerhubpwd}'
				}
				sh 'docker push shubhamwalunj25/testdocker_2:latest'
        	}       	
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
