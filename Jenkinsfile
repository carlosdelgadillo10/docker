
def app
pipeline {
    agent any
    environment {
        WORKSPACE_DIR = "C:/ProgramData/Jenkins/.jenkins/workspace/docker"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    app = docker.build("carlosdelgadillo/suma_windows")
                }
            }
        }
        stage('Push image') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
                    app.push("${env.BUILD_NUMBER}")
                    }
                }
            }
        }   
    }
    


