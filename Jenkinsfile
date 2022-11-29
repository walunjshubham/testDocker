pipeline {
    agent any
    tools{
    maven 'MAVEN'
    }
    stages {
     stage('Clone repository') {
        /* Cloning the Repository to our Workspace */

        checkout scm
    }
        stage('Build') { 
            steps {
            bat 'mvn clean install'
            }
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
    post{
    always{
    	junit(
    	allowEmptyResults:true,
    	testResults:'*test-reports.xml'
    	)
    }
    }

}
