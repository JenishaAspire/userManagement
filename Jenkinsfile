def dockerRun = 'docker-compose up --build; bash -l'
pipeline {
    agent any
    stages  {
        stage('checkout') {
            steps {
               git credentialsId: 'gitHub', url: 'https://github.com/jenishapriscilla/DeploymentFundamental'
            }
        }
        stage('deploy') {
            steps {
                sh 'docker-compose up'
            }
        }
    }
}
