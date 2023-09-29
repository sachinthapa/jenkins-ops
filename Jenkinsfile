pipeline {
    environment {
        dockerimagename = "thapasachin/market-data"
        dockerImage = ""
    }

    agent any

    stages {
        stage('Checkout Source') {
          steps {
            git 'https://github.com/sachinthapa/jenkins-ops'
          }
        }
        stage('Build image') {
            steps{
                script {
                    dockerImage = docker.build dockerimagename
                }
            }
        }

        stage('Pushing Image') {
            environment {
                registryCredential = 'docker-credentials'
                }
            steps{
                script {
                    docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
                        dockerImage.push("v3")
                    }
                }
            }
        }
    }


}
