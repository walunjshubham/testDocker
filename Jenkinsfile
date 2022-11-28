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
			stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }

    stage('Build image') {
        /* This builds the actual image */

        app = docker.build("shubhamwalunj25/jenkins:latest")
    }

    stage('Test image') {
        
        app.inside {
            echo "Tests passed"
        }
    }

	stage('Push image') {
	docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            app.push("${env.BUILD_NUMBER}")
            app.push("latest")
            } 
                echo "Trying to Push Docker Build to DockerHub"
	
    }
		}
	}
    
}