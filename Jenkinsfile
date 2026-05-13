pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/YOUR_USERNAME/YOUR_REPO.git',
                credentialsId: 'github-token'
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                sudo rm -rf /usr/share/nginx/html/*
                sudo cp -r * /usr/share/nginx/html/
                '''
            }
        }

    }
}
