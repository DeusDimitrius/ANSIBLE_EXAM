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

       httpRequest responseHandle: 'NONE', timeout: 2500, url: 'http://127.0.0.1:7001', validResponseCodes: '200', consoleLogResponseBody: true
     }
    }
   }
}
