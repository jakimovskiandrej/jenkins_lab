pipeline {
    agent any
    stages {
        stage('Build Image') { 
            steps { 
                sh 'docker build -t jakimovskiandrej/my-nginx-app .' 
            } 
        }
        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('', 'docker-hub-creds') {
                        docker.image('jakimovskiandrej/my-nginx-app').push('latest')
                    }
                }
            }
        }
    }
}