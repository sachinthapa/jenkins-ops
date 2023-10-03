// pipeline {
//     environment {
//         dockerimagename = "thapasachin/market-data"
//         dockerImage = ""
//     }
//
//     agent any
//
//     stages {
//         stage('Checkout Source') {
//           steps {
//             git 'https://github.com/sachinthapa/jenkins-ops'
//           }
//         }
//
//         // def service = "market-data:${tag}"
//         container('docker') { 
//             stage('Build image') {
//                 steps{
//                     sh('docker build -t thapasachin/market-data:trash .')
//                 }
//             }
//         }
//         //
//         // stage('Pushing Image') {
//         //     environment {
//         //         registryCredential = 'docker-credentials'
//         //         }
//         //     steps{
//         //         script {
//         //             docker.withRegistry( 'https://registry.hub.docker.com', registryCredential ) {
//         //                 dockerImage.push("v3")
//         //             }
//         //         }
//         //     }
//         // }
//     }
//
// }


// }

podTemplate {
    node(POD_LABEL) {
        stage('Run shell') {
            sh 'echo hello world'
        }
    }
}

withPod {
  node('pod') {
    def tag = "trash"
    // def tag = "${env.BRANCH_NAME}.${env.BUILD_NUMBER}"
    def service = "market-data:${tag}"

    // checkout scm

    // container('docker') {
    //   stage('Build') {
    //     sh("docker build -t ${service} .")
    //   }
    // }
  }
}
