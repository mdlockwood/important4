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
          junit 'test.xml'
          junit 'test2.xml'

        }

      }
      steps {
        input(message: 'Release to Production', id: 'myid', ok: 'Ok', submitter: 'mdlockwood')
        echo 'Hello Deploy'
        sleep 10
        sh '''echo \'<testsuite tests="3">\' > test.xml
echo \'<testcase classname="DeployWebServer" name="DeployWebServer"/>\' >> test.xml
echo \'<testcase classname="DeployDatabase" name="DeployDatabase"/>\' >> test.xml
echo \' <testcase classname="StartServices" name="StartServices">\' >> test.xml
echo \'<failure type="Service Failed to start cuz it does not want to"> The service is being stubborn </failure>\' >> test.xml
echo \'</testcase>\' >> test.xml
echo \'</testsuite>\' >> test.xml

echo \'<testsuite tests="5">\' > test2.xml
echo \'<testcase classname="DeployWebServer" name="CopyWebsphereSource"/>\' >> test2.xml
echo \'<testcase classname="DeployWebServer" name="InstallWebSphere"/>\' >> test2.xml
echo \'<testcase classname="DeployDatabase" name="CreateSchema"/>\' >> test2.xml
echo \'<testcase classname="DeployDatabase" name="SecureTableSpaces"/>\' >> test2.xml
echo \' <testcase classname="StartServices" name="StartServices">\' >> test2.xml
echo \'<failure type="Service Failed to start cuz it does not want to"> The service is being REALLY stubborn </failure>\' >> test2.xml
echo \'</testcase>\' >> test2.xml
echo \'</testsuite>\' >> test2.xml
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
