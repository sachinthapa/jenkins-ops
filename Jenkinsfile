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


        stage('Docker node test') {
             agent {
                docker-agent{
                    steps {
                        sh 'docker -v'
                    }
                }
            }
        }
    }
}
        // def service = "market-data:${tag}"



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
