pipeline {
    agent any

    stages {

        stage('Checkout') {
            steps {
                git 'https://github.com/USERNAME/REPO.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t USERNAME/REGISTER_ROLL .'
            }
        }

        stage('Login DockerHub') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', usernameVariable: 'USER', passwordVariable: 'PASS')]) {
                    sh 'echo $PASS | docker login -u $USER --password-stdin'
                }
            }
        }

        stage('Push Image') {
            steps {
                sh 'docker push USERNAME/REGISTER_ROLL'
            }
        }

    }
}
