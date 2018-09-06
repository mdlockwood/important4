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
      post {
        always {
	  junit 'test3.xml'

        }

      }
      steps {
        input(message: 'Release to Production', id: 'myid', ok: 'Ok', submitter: 'mdlockwood')
        echo 'Hello Deploy'
        sleep 10
	sh '''echo \'<testsuite tests="5">\' > test3.xml
echo \'<testcase classname="DeployWebServer" name="Test01"/>\' >> test3.xml
echo \'<testcase classname="DeployWebServer" name="Test02"/>\' >> test3.xml
echo \'<testcase classname="DeployDatabase" name="Test03"/>\' >> test3.xml
echo \'<testcase classname="DeployDatabase" name="Test04"/>\' >> test3.xml
echo \' <testcase classname="StartServices" name="Test05">\' >> test3.xml
echo \'<failure type="General Failure"> Please fix this junk</failure>\' >> test3.xml
echo \'</testcase>\' >> test3.xml
echo \'</testsuite>\' >> test3.xml
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
