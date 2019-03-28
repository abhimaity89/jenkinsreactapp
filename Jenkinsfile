pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh 'npm install'
        echo 'NPM Packages have been loaded'
      }
    }
    stage('Test') {
      steps {
        sh 'bash ./jenkins/scripts/test.sh'
        input(message: 'Is test successfull?Ready and continue?', ok: 'Yes and continue to publish')
      }
    }
    stage('Deliver and Stop') {
      steps {
        sh 'bash ./jenkins/scripts/deliver.sh'
        input(message: 'Have you tested React app?', ok: 'Yes. I have successfully tested and stopped the server')
        sh 'bash ./jenkins/scripts/kill.sh'
      }
    }
  }
  environment {
    CI = 'true'
    HOME = '.'
    PORT_NUMBER = '9090'
  }
}