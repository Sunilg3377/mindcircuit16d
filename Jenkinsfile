pipeline {
    agent any

    stages {
        stage('Clone SCM') {
            steps {
                echo 'This stage clone sc from git repo'
				git branch: 'main', url: 'https://github.com/Sunilg3377/mindcircuit16d.git'
            }
        }
		
        stage('Buils Maven tool') {
            steps {
                echo 'build with maven tool'
				sh 'mvn clean install'
            }
        }

        stage('deploy web server') {
            steps {
                echo 'deployed with tomcat'
				deploy adapters: [tomcat9(alternativeDeploymentContext: '', credentialsId: 'tomcat', path: '', 
				url: 'http://98.81.160.184:8080/')], contextPath: 'mc-apps', war: '**/*.war'
            }
        }
	
    
    }
}
