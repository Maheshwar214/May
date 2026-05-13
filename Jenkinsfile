pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git branch: 'main',
                url: 'https://github.com/Maheshwar214/May.git',
                credentialsId: 'github-token'
            }
        }

        stage('Deploy Website') {
            steps {
                sh '''
                sudo rm -rf /usr/share/nginx/html/*
                sudo cp -r ./* /usr/share/nginx/html/
                sudo chmod -R 755 /usr/share/nginx/html
                '''
            }
        }
    }
}
