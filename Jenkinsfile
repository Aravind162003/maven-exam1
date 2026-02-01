pipeline {
    agent any

    environment {
        IMAGE_NAME = "aravind2003/new-maven"
    }

    stages {

        stage('Checkout') {
            steps {
                git url: 'https://github.com/Aravind162003/maven-exam1', branch: 'master'
            }
        }

        stage('Build Maven Project') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
        }

        stage('Build Docker Image') {
            steps {
                script {
                    dockerImage = docker.build("${IMAGE_NAME}:latest")
                }
            }
        }

        stage('Push Docker Image') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'docker') {
                        dockerImage.push('latest')
                    }
                }
            }
        }
    }
}
 
