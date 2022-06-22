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
        stage('deploy') {
            steps {
		 withCredentials([aws(accessKeyVariable:'AWS_ACCESS_KEY_ID', credentialsId:'JenishaAwsEC2', secretKeyVariable:'AWS_SECRET_ACCESS_KEY')]) {
                     sh 'aws ec2 describe-instances'
                 }
	    }
        }
    }
}
