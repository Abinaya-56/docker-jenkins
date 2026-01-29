pipeline {
    agent any

    stages {

        stage('Build Image') {
            steps {
                sh 'docker build -t abinaya242/jenkins-demo:latest .'
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
                sh 'docker push abinaya242/jenkins-demo:latest'
            }
        }
    }
}
