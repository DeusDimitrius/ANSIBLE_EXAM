pipeline {
  agent any

   stages {

    stage ('Run') {
     steps {
             sh "ansible-playbook site.yml -i hosts"
     }
    }

    stage ('Health check') {
     steps {
             sleep 30
           }

     steps {
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP1:5000', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP2:5000', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP2:5000', validResponseCodes: '200', consoleLogResponseBody: true
      }
    }
   }
}
