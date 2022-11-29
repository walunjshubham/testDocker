pipeline {
    agent any
    tools{
    maven 'MAVEN'
    }
    stages {
        stage('Build') { 
            steps {
               sh 'mvn clean install'
            }
        }        
        stage('push docker img to dockerhub') { 
        steps{
        	script{
            docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
            docker.image("shubhamwalunj25/testdocker_1:${TAG}").push()
            docker.image("shubhamwalunj25/testdocker_1:${TAG}").push("latest")
            }
            } 
            }
        }
        stage('Deploy'){
        steps{
        	sh "docker stop testdocker_1 | true"
        	sh "docker rm testdocker_1 | true"
        	sh "docker run --name testdocker_1 -d -p 9004:8080 shubhamwalunj25/testdocker_1"
        }
        }
    }

}
