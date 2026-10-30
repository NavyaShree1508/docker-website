pipeline {
    agent any

    stages {
        stage('Check Docker') {
            steps {
                bat 'docker --version'
            }
        }

        stage('Build Docker Image') {
            steps {
                bat 'docker build -t college-website .'
            }
        }

        stage('Deploy Website') {
            steps {
                script {
                    bat(script: 'docker rm -f college-website-container', returnStatus: true)
                }
                bat 'docker run -d -p 8082:80 --name college-website-container college-website'
            }
        }
    }
}
