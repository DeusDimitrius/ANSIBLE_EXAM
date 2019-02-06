pipeline {
  agent any

   stages {

    stage ('Install') {
     steps { 
             sh "ansible-galaxy install -f -r requirements.yml --roles-path=roles"
     }
    }

    stage ('Run') {
     steps {
             sh "ansible-playbook -i site.yml hosts.yml"
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
