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
                sh 'docker build -t Sample-image .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop Sample || true
                docker rm Sample || true
                docker run -d -p 80:80 --name Sample Sample-image
                '''
            }
        }
    }
}
