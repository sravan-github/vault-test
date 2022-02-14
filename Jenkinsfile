pipeline {
    //agent any
    
    agent {
        docker { image 'sravangcpdocker/toolkit:10' }
    }
    stages {
        stage('git-clone') {
            steps {
                sh '''
                   #!/bin/bash
                   sudo su ununtu
                   git clone https://github.com/sravan-github/vault-test.git
                   ls -ltr
                   pwd
                   '''
            }
        }
        stage('vault') {
            steps {
                sh '''
                ansible-playbook vault.yml
                #ansible-vault decrypt key.json --vault-password-file pass --output key2.json              
                '''
            }
          }
        
    }

post {
        always {
            cleanWs deleteDirs: true
        }
     }
}
