pipeline {
    agent any

    stages {
        stage('Build app') {
            steps {
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/NinadTippat/POE.git']])
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    bat 'docker build -t jenkinsdocker .'
                }
            }
        }

        stage('Rename Image Tag') {
            steps {
                script {
                    bat 'docker tag jenkinsdocker ninadtippat/jenkinsdockerapp:img1'
                }
            }
        }

        stage('Push Image to Docker Hub') {
            steps {
                script {
                    bat 'docker login -u ninadtippat -p Ninad@2003'
                    bat 'docker push ninadtippat/jenkinsdockerapp:img1'
                }
            }
        }
        
    }
}
