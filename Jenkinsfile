pipeline {
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
}
