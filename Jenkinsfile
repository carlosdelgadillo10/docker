
pipeline {
    agent any
    environment {
        WORKSPACE_DIR = "C:/ProgramData/Jenkins/.jenkins/workspace/docker"
    }
    stages {
        stage('Build') {
            steps {
                script {
                    docker.build("carlosdelgadillo/suma_windows")
                }
            }
        }
        stage('Scan') {
            steps {
                script {
                    docker.withRegistry('https://registry.hub.docker.com', 'docker-credentials') {
                        bat """
                        docker run -d -t ^
                            -w "${env.WORKSPACE_DIR}" ^
                            -v "${env.WORKSPACE_DIR}:${env.WORKSPACE_DIR}" ^
                            mi-app:latest
                        """
                    }
                }
            }
        }
    }
}
