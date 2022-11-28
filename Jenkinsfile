pipeline {
<<<<<<< HEAD
    agent any 
    stages {
        stage('Build') { 
            steps {
               checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/walunjshubham/testDocker']]])sh 'mvn clean install'
				sh 'mvn clean install'
            }
        }
        stage('Test') { 
            steps {
                // 
            }
        }
        stage('Deploy') { 
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
        }
    }
=======
    agent any
    tools{
    	maven 'MAVEN'
    }
	stages{
		stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }
		
		stage('Build Maven'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/walunjshubham/testDocker']]])sh 'mvn clean install'
				sh 'mvn clean install'
			}
			
	}
	}   
>>>>>>> 9869cdcdf74fba32d88942b94b6e403d115ded3f
}
