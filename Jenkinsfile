pipeline {
    agent any
    tools {dockerTool  "myDocker" } 
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-credentials')
        service = "market-data"
        tagToDeploy = "v3"
    }
    stages {
        stage('Checkout Source') {
            steps {
                git 'https://github.com/Bravinsimiyu/jenkins-kubernetes-deployment.git'
            }
        }

        stage('Build') {
            steps {
                sh 'docker build -t market-data:v3 market-data-final/.'
            }
        }

        stage('Publish') {
             withDockerRegistry(registry: [credentialsId:'docker-credentials']) {
                 sh "docker tag ${service} ${tagToDeploy}"
                 sh "docker push ${tagToDeploy}"
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
