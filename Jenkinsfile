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
      parallel {
        stage('Test') {
          steps {
            echo 'Hello Test'
            echo 'Hello Tets'
          }
        }
        stage('Test-P') {
          steps {
            echo 'Hello Test-P'
            sleep 10
          }
        }
      }
    }
    stage('Deploy') {
      steps {
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