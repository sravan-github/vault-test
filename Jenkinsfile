pipeline {
    //agent any
    
    agent {
        docker { image 'sravangcpdocker/toolkit:11' }
    }
    stages {
        stage('git-clone') {
            steps {
                sh '''
                   #!/bin/bash
                   git clone https://github.com/sravan-github/vault-test.git
                   ls -ltr
                   pwd
                   '''
            }
        }
        stage('vault') {
            steps {
                sh '''
                chmod +x vault.yml
                chmod +x key.json
                ls -ltr
                ansible-playbook vault.yml
                #ansible-vault decrypt key.json --vault-password-file pass --output key2.json   
                ls -ltr
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
