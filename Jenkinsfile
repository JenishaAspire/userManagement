pipeline {
    agent any
    stages  {
        stage('checkout') {
            steps {
               git credentialsId: 'gitHub', url: 'https://github.com/JenishaAspire/userManagement'
            }
        }
        stage('setup') {
            steps {
                sh 'docker system prune -a -f'
                sh 'docker-compose run php composer install'
            }
        }
        stage('deploy') {
            steps {
		 sshagent(credentials :['JenishaAspireAws']) {  
		    sh "DOCKER_HOST='ssh -o StrictHostKeyChecking=no ec2-user@ec2-3-87-199-183.compute-1.amazonaws.com' docker-compose up"
		 }
	    }
        }
    }
}
