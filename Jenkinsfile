pipeline {
    agent any
    environment {
	AWS_DEFAULT_REGION='us-east-1'
    }
    stages  {
        stage('checkout') {
            steps {
               git credentialsId: 'gitHub', url: 'https://github.com/JenishaAspire/userManagement'
            }
        }
	stage('de') {
            steps {
		  sh "pwd"
	    }
        }
        stage('deploy') {
            steps {
		 sshagent(['JenishaAspireAws']) {
       			sh "ssh -o StrictHostKeyChecking=no ec2-user@44.206.230.72 git credentialsId: 'gitHub', url: 'https://github.com/JenishaAspire/userManagement"
     		 }
	    }
        }
    }
}
