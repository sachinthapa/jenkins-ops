pipeline {
    agent any
    // tools {dockerTool  "myDocker" } 
    environment{
        DOCKERHUB_CREDENTIALS = credentials('docker-credentials')
        service = "market-data"
        tagToDeploy = "thapasachin/market-data"
    }
    stages {
        stage('Checkout Source') {
            steps {
                git 'https://github.com/Bravinsimiyu/jenkins-kubernetes-deployment.git'
            }
        }

        // stage('Build') {
        //     steps {
        //         sh 'docker build -t market-data market-data-final/.'
        //     }
        // }
        //
        // stage('login') {
        //     steps {
        //         sh 'echo $DOCKERHUB_CREDENTIALS_PSW| docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
        //     }
        // }
        //
        // stage('Publish') {
        //     steps{
        //          sh "docker tag ${service} ${tagToDeploy}"
        //          sh "docker push ${tagToDeploy}"
        //      }
        // }

        stage('Deploy') {
            steps{
                withKubeConfig([credentialsId: 'kube-secret', serverUrl: 'https://192.168.1.67:6443']) {
                    // sh 'curl -LO "https://storage.googleapis.com/kubernetes-release/release/v1.20.5/bin/linux/amd64/kubectl"'
                    //  sh 'chmod u+x ./kubectl'
                     sh "sed -i.bak 's#BUILD_TAG#${tagToDeploy}#' deploy/staging/*.yml"
                     sh "./kubectl apply -f deploy/staging/ -n staging"
                 }
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
