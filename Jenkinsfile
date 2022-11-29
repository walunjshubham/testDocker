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
        	bat 'docker build -t shubhamwalunj25/docker-project .'
        	}
            }
        }
        stage('Push image to docker hub'){
        steps{
 			script{
   				 bat 'docker login -u shubhamwalunj25 -p Shubham@2144'
				bat 'docker push shubhamwalunj25/docker-project'
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
