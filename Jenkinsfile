pipeline {
    //agent any
    
    agent {
        docker { image 'sravangcpdocker/terraform:7' }
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
                ansible-playbook -b vault.yml
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
