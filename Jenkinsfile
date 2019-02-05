pipeline {
  agent any

   stages {

    stage ('Run') {
     steps {
             sh "ansible-playbook -i site.yml"
     }
    }

    stage ('Health check') {
      sleep 30

       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP1:5000', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP2:5000', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP2:5000', validResponseCodes: '200', consoleLogResponseBody: true
      }
    }
}
