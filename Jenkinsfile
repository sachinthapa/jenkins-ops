pipeline {
    agent any
    tools {dockerTool  "myDocker" } 
    stages {
        stage('Build') {
            agent {
                docker{
                }
            }
            // steps {
            //     sh("docker -v")
            //     // sh 'docker-v'
            // }
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
