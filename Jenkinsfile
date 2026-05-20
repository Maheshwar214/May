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

        stage('Remove Old Container') {
            steps {
                sh '''
                docker rm -f sample || true
                '''
            }
        }

        stage('Run Containers') {
    steps {
        sh '''
        docker compose down
        docker compose up -d --build
        '''
    }
}

        stage('Clean Unused Images') {
            steps {
                sh 'docker image prune -af'
            }
        }
    }
}
