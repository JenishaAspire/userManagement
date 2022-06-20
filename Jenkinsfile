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
            def dockerRun = 'docker-compose up'
            sshagent(['JenishaAspireAws']) {  
                sh "ssh -o StrictHostKeyChecking=no ec2-user@1ec2-3-87-199-183.compute-1.amazonaws.com ${dockerRun}"
            }
        }
    }
}
