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

        // def service = "market-data:${tag}"
        container('docker') { 
            stage('Build image') {
                steps{
                    sh('docker build -t thapasachin/market-data:trash .')
                }
            }
        }
        //
        // stage('Pushing Image') {
        //     environment {
        //         registryCredential = 'docker-credentials'
        //         }
        //     steps{
        //         script {
        //             docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
        //                 dockerImage.push("v3")
        //             }
        //         }
        //     }
        // }
    }


}
