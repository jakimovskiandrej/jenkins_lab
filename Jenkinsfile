pipeline {
    agent any
    stages {
        stage('Clone') {
            steps {
                checkout scm
            }
        }
        stage('Build Image') { 
            steps { 
                sh '/usr/bin/docker build -t jakimovskiandrej/my-nginx-app .' 
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