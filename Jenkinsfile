pipeline {
    agent any

    stages {

        stage('Checkout from GitHub') {
            steps {
                git branch: 'master',
                    url: 'https://github.com/sricharnitha13/node-docker-app.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat '''
                docker build -t node-docker-app:%BUILD_NUMBER% .
                docker tag node-docker-app:%BUILD_NUMBER% sricharnitha/node-docker-app:%BUILD_NUMBER%
                '''
            }
        }

        stage('Create container') {
            steps {
                bat 'docker run -d -p 3000:8080 sricharnitha/node-docker-app:%BUILD_NUMBER%'
            }
        }

    }
}
