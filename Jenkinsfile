def dockerRun = 'docker-compose up --build; bash -l'
pipeline {
    agent any
    stages  {
        stage('checkout') {
            steps {
               git credentialsId: 'gitHub', url: 'https://github.com/JenishaAspire/userManagement'
            }
        }
        stage('Test') {
            steps {
                sh 'echo "Test"'
            }
        }
        stage('deploy') {
            steps {
                sh 'docker-compose run php composer update'
                sh 'docker-compose up'
            }
        }
    }
}
