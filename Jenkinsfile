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
             sh "ansible-playbook -i hosts site.yml"
     }
    }    

    stage ('Health check') {
     steps {
             sleep 30

       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://...:5001', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://...:5002', validResponseCodes: '200', consoleLogResponseBody: true
       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://...:5003', validResponseCodes: '200', consoleLogResponseBody: true
     }
    }
   }
}
