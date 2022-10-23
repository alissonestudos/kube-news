pipeline {
    agent any
    stages {
        stage ('Build Docker Image'){
            steps {
                script {
                   dockerapp = docker.build("alissonteixeira2805/kube-news:${env.BUILD_ID}", '-f ./src/Dockerfile ./src')
                }
            }
        }

        stage ('Push Docker Image'){
            steps{
                script {
                    docker.whithRegistry('https://registry.hub.docker.com', 'dockerhub')
                        dockerapp.push('latest')
                        dockerapp.push("${env.BUILD_ID}")
                }
            }
        }
    }
}