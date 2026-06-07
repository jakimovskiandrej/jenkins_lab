pipeline {
    agent any
    stages {
        stage('Clone Repository') { steps { checkout scm } }
        stage('Build Image') { steps { sh 'docker build -t my-nginx-app .' } }
        stage('Push Image') {
            steps {
                script {
                    docker.withRegistry('', 'docker-hub-credentials') {
                        docker.image('my-nginx-app').push('latest')
                    }
                }
            }
        }
    }
}