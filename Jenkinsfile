pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Maheshwar214/May.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build --no-cache -t sample-image .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh '''
                docker stop sample || true
                docker rm sample || true
                '''
            }
        }

        stage('Run New Container') {
            steps {
                sh '''
                docker run -d -p 9090:80 --name sample sample-image
                '''
            }
        }

        stage('Clean Unused Images') {
            steps {
                sh 'docker image prune -f'
            }
        }
    }
}
