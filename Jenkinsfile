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
        withCredentials([string(credentialsId: 'dockerpwd', variable: 'pwd')]) {
    		bat "docker login -u shubhamwalunj25 -p ${pwd}"
				}
        
 			script{
				bat 'docker push shubhamwalunj25/docker-project'
        	}       	
        	 }
        }
		 stage('Deploy'){
        steps{
        script{
        	bat "docker run -p 8081:8081 -d --name docker-project shubhamwalunj25/docker-project"
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
