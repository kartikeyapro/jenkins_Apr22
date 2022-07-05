node {
 
    stage('Git Clone') 
	{
      git changelog: false, credentialsId: 'git', poll: false, url: 'https://github.com/kartikeyapro/ks.git'
    }
    stage('Maven Clean') {
      sh 'mvn clean'
    }
	stage('Sonar Scan'){
		sh 'mvn sonar:sonar -Dsonar.host.url=http://192.168.29.24:9000 -Dsonar.login=ebbd7653928d686151e5a8137327e78db120cf04'
	}
    stage('Code Validate') {
	
        sh 'mvn validate'
    }
	stage('Code Complie') {
	
        sh 'mvn compile'
    }
	stage('Code Test') {
	
        sh 'mvn test'
    }
	stage('Code Package') {
	
        sh 'mvn package'
    }
}

