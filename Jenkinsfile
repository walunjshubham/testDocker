pipeline {
    agent any
    tools{
    	maven 'maven_3_8_6'
    }
	stages{
		stage('Build Maven'){
			steps{
				checkout([$class: 'GitSCM', branches: [[name:'*master']], extension: [], userRemoteConfigs: [[url:'https://github.com/walunjshubham/testDocker']]])
				sh 'mvn clean install'
			}
		}
	}
    
}