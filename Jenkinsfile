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
        // container('docker') { 
            stage('Build image') {
                steps{
                    sh('docker build -t thapasachin/market-data:trash .')
                }
            }
        // }
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


// }

// podTemplate(containers: [
//     containerTemplate(
//         name: 'jnlp', 
//         image: 'jenkins/inbound-agent:latest'
//         )
//   ]) {
//
//     node(POD_LABEL) {
//         stage('Get a Maven project') {
//             container('jnlp') {
//                 stage('Shell Execution') {
//                     sh '''
//                     echo "Hello! I am executing shell"
//                     '''
//                 }
//             }
//         }
//
//     }
// }
