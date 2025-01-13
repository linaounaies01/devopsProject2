pipeline {
    agent any
    triggers {
        pollSCM('H/5 * * * *')
    }
    environment {
        DOCKERHUB_CREDENTIALS = credentials('dockerhub') // ID pour Docker Hub
        IMAGE_NAME_SERVER = 'linaounaies760/mern-server' // Remplacez [username] par votre utilisateur Docker Hub
        IMAGE_NAME_CLIENT = 'linaounaies760/mern-client'
    }
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/linaounaies01/devopsProject2'
            }
        }
        stage('Build Server Image') {
            steps {
                dir('server') {
                    script {
                        dockerImageServer = docker.build("${IMAGE_NAME_SERVER}")
                    }
                }
            }
        }
        stage('Build Client Image') {
            steps {
                dir('client') {
                    script {
                        dockerImageClient = docker.build("${IMAGE_NAME_CLIENT}")
                    }
                }
            }
        }
      
        
        stage('Push Images to Docker Hub') {
            steps {
                script {
                    docker.withRegistry('', 'dockerhub') {
                        dockerImageServer.push()
                        dockerImageClient.push()
                    }
                }
            }
        }
    }
}
