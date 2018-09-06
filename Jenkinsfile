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
        echo 'Hello Test'
      }
    }
    stage('Deploy') {
      steps {
        input(message: 'Release to Production', id: 'myid', ok: 'Ok', submitter: 'mdlockwood')
        echo 'Hello Deploy'
        sleep 10
        sh '''echo a
echo b
echo c
'''
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