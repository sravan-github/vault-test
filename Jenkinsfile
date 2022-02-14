pipeline {
    agent {
        docker { image 'sravangcpdocker/terraform:2' }
    }
    stages {
        stage('git-clone') {
            steps {
                sh '''
                   #!/bin/bash
                   git clone https://github.com/sravan-github/vault-test.git
                   ls -ltr
                   '''
            }
        }
        stage('vault') {
            steps {
                sh '''
                ansible-playbook vault.yml
                #ansible-vault decrypt key.json --vault-password-file pass --output key2.json
                ls -ltr
                cd vault-test
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
