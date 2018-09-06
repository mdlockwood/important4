pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Hello Build'
        sleep 10
      }
    }
    stage('Test') {
      steps {
        echo 'Hello Test'
        echo 'Hello Tets'
      }
    }
    stage('Deploy') {
      steps {
        input(message: 'I need INPUT', id: 'myid', ok: 'Ok', submitter: 'idk', submitterParameter: 'idk')
        echo 'Hello Deploy'
        sleep 10
      }
    }
    stage('End') {
      steps {
        echo 'Hello End'
        sleep 10
      }
    }
  }
}