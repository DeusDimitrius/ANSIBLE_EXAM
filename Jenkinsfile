pipeline {
  agent any

   stages {

    stage ('Run') {
     steps {
             sh "ansible-galaxy install --force -r requirements.txt --roles-path=roles-remote"
             sh "ansible-playbook site.yml -i hosts"
     }
    }

    stage ('Health check') {
     steps {
             sleep 30

       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP1:5000', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP2:5000', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://IP2:5000', validResponseCodes: '200', consoleLogResponseBody: true
     }
    }
   }
}
