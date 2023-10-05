// pipeline {
//     agent any
//     tools {dockerTool  "myDocker" } 
//     stages {
//         stage('Checkout Source') {
//             steps {
//                 git 'https://github.com/Bravinsimiyu/jenkins-kubernetes-deployment.git'
//             }
//         }
//
//         stage('Build') {
//             steps {
//                 sh 'docker build -t market-data:v3 market-data-final/.'
//             }
//         }
//     }
// }

def withPod(body) {
     podTemplate(label: 'pod', serviceAccount: 'jenkins', containers: [
         containerTemplate(name: 'docker', image: 'docker', command: 'cat',ttyEnabled: true)
    //  containerTemplate(name: 'kubectl', image: 'morganjbruce/kubectl',
    // command: 'cat', ttyEnabled: true)
     ],
     volumes: [
         hostPathVolume(mountPath: '/var/run/docker.sock', hostPath:'/var/run/docker.sock'),
     ]
     ) { body() }
}

withPod {
     node('pod') {
         // def tag = "${env.BRANCH_NAME}.${env.BUILD_NUMBER}"
         // def service = "market-data:${tag}"

         checkout scm
         container('docker') {
             stage('Build') {
                 sh "docker build -t market-data:t1 market-data-final/."
            }
         }
     }
}

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
