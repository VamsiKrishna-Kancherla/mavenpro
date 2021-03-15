pipeline {
    agent any 
    stages {
        stage('clean & clone') { 
            steps {
                sh "mvn clean compile"
                
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
  
