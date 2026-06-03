pipeline {
    agent any

    environment {
        IMAGE_NAME = "jenkins-demo"
    }

    stages {

        stage('Checkout Code') {
            steps {
                git 'https://github.com/your-username/your-repo.git'
            }
        }

        stage('Build App') {
            steps {
                sh 'npm install'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t jenkins-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop app || true
                docker rm app || true
                docker run -d -p 3000:3000 --name app jenkins-demo
                '''
            }
        }
    }
}
