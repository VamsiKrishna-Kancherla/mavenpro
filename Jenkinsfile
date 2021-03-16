pipeline {
    agent any 
    stages {
        stage('clean & clone') { 
            steps {
                sh "mvn compile"
                
            }
        }
        stage('Test') { 
            steps {
                sh "mvn test"
            }
        }
        stage('Package') { 
            steps {
                sh "mvn package"
            }
        }
	 stage('Build & Docker image') {
            steps {
                sh "docker build -t vamsi1krishna/mavenpro_image:${BUILD_NUMBER} ."
            }
	}
	 stage('login') {
            steps {
		withCredentials([string(credentialsId: 'DockerID', variable: 'Dockerpw')])
                sh "docker login -u vamsi1krishna -p ${Dockerpw}"
            }
	}
	 stage('push') {
            steps {
                sh "docker push vamsi1krishna/mavenpro_image:${BUILD_NUMBER}"
            }
	} 
        stage('Archiving') { 
            steps {
                archiveArtifacts '**/target/*.jar'
            }
        }
        
    }
}
  
