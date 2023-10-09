FROM jenkins/jenkins
USER root
RUN apt-get update -qq \
    && apt-get install -qqy apt-transport-https ca-certificates curl gnupg2 software-properties-common
RUN curl -fsSL https://download.docker.com/linux/debian/gpg | apt-key add -
RUN add-apt-repository \
   "deb [arch=amd64] https://download.docker.com/linux/debian \
   $(lsb_release -cs) \
   stable"
RUN apt-get update  -qq \
    && apt-get -y install docker-ce
RUN usermod -aG docker jenkins
RUN curl -LO https://dl.k8s.io/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl; chmod +x ./kubectl;mkdir -p ~/.local/bin; mv ./kubectl ~/.local/bin

# docker run -d -p 8080:8080 -v /var/run/docker.sock:/var/run/docker.sock -v jenkins_home:/var/jenkins_home custom-jenkins-docker
#
#
# pipeline {
#   agent any
#   stages {
#     stage('Apply Kubernetes files') {
#       steps {
#         withKubeConfig([credentialsId: 'kube-secret', serverUrl: '192.168.1.67:6443']) {
#           sh  'curl -LO https://dl.k8s.io/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl'
#         //   sh 'mv ./kubectl /usr/local/bin/kubectl'
#           //sh 'curl -LO https://dl.k8s.io/release/v1.28.2/bin/linux/amd64/kubectl'
#           sh 'chmod u+x ./kubectl'
#           sh './kubectl version'
#         }
#       }
#     }
