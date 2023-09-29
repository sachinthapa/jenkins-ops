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

def withPod(body) {
 podTemplate(
        label: 'pod', 
        serviceAccount: 'jenkins', 
        containers: [
                containerTemplate(name: 'docker', image: 'docker', command: 'cat',ttyEnabled: true)
                //,
                // containerTemplate(name: 'kubectl', image: 'lachlanevenson/k8s-kubectl', command: 'cat', ttyEnabled: true)
                ], 
        volumes: [hostPathVolume(mountPath: '/var/run/docker.sock', hostPath:'/var/run/docker.sock'),]
     ){ body() }
}

withPod {
  node('pod') {
    def tag = "trash"
    // def tag = "${env.BRANCH_NAME}.${env.BUILD_NUMBER}"
    def service = "market-data:${tag}"

    checkout scm

    container('docker') {
      stage('Build') {
        sh("docker build -t ${service} .")
      }
    }
  }
}
