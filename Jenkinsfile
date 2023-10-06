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
                sh 'docker build -t market-data market-data-final/.'
            }
        }

        stage('login') {
            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS | docker login -u $DOCKERHUB_CREDENTIALS --password-stdin'
            }
        }

        stage('Publish') {
            steps{
                 sh "docker tag ${service} ${tagToDeploy}"
                 sh "docker push ${tagToDeploy}"
             }
        }
    }

    post{
        always{
            sh 'docker logout'
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
