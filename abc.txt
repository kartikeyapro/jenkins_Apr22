pipeline {
    agent {
		label 'Jenkins-node1'
	}

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
             git changelog: false, credentialsId: 'git', poll: false, url: 'https://github.com/kartikeyapro/ks.git'   
            }           
            }
        stage('Maven Clean') {
            steps {
             sh 'mvn clean'   
            }           
            }
        stage('SonarQube') {
            steps {
                sh 'mvn sonar:sonar -Dsonar.host.url=http://192.168.29.24:9000 -Dsonar.login=ebbd7653928d686151e5a8137327e78db120cf04'
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
