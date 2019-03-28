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
  }
  environment {
    CI = 'true'
    HOME = '.'
    PORT_NUMBER = '9090'
  }
}