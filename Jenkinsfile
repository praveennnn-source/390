pipeline {
    agent any

    stages {

        stage('Clone Repository') {
            steps {
                git ''
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t static-website .'
            }
        }

        stage('Stop Old Container') {
            steps {
                sh 'docker rm -f static-container || true'
            }
        }

        stage('Run New Container') {
            steps {
                sh 'docker run -d -p 80:80 --name static-container static-website'
            }
        }
    }
}
