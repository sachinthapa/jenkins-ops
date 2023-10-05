pipeline {
    agent any
    tools {dockerTool  "myDocker" } 
    stages {

        stage('Checkout Source') {
            steps {
                git 'https://github.com/Bravinsimiyu/jenkins-kubernetes-deployment.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t market-data:v3'
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
