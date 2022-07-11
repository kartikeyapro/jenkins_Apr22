pipeline {
	agent any

    tools {
        maven 'Maven 3.0.5'
    }

    stages {
		stage('Maven Version') {
            steps {
            sh 'mvn --version'
            }           
            }
		stage('Hostname') {
            steps {
            sh 'hostname'
            }           
            }
        stage('Code Clone') {
            steps {
             git branch: 'main', credentialsId: 'git', url: 'https://github.com/kartikeyapro/ks.git'  
            }           
            }
        stage('Maven Clean') {
            steps {
             sh 'mvn clean'   
            }           
            }
        stage('Maven Validate') {
            steps {
                sh 'mvn validate'
            }           
            }
        stage('Maven Compile') {
            steps {
              sh 'mvn compile'  
            }           
            }
       
        stage('Maven Test') {
            steps {
                sh 'mvn test'
            }           
            }
			
        stage('Maven Package') {
            steps {
               sh 'mvn package'  
            }           
            }
		
		
		
    }
}
