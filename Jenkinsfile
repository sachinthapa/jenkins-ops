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
    }
}
