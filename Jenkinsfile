pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh 'docker build -t yourdockerhubusername/jenkins-demo:latest .'
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
                sh 'docker push yourdockerhubusername/jenkins-demo:latest'
            }
        }
    }
}
