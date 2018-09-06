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
	  junit 'test3.xml'

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

echo \'<testsuite tests="5">\' > test3.xml
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
