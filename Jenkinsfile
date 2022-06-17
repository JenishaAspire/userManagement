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
                sh 'docker-compose run php composer update symfony/flex --no-plugins --no-scripts'
                sh 'docker-compose run php composer install'
            }
        }
        stage('deploy') {
            steps {  
                sh 'docker-compose up'
            }
        }
    }
}
