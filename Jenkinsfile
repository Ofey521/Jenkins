pipeline{
    agent{
        label "ansible"
    }
    environment {
        ansible_private_key=credentials('ansible-priv')
        ofey=credentials('ofey_pass')
    }
    stages{
        stage('Pull') {
            steps {
                dir('ansible'){
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'ansible-priv' ,url: 'git@github.com:Ofey521/Ansible.git']]])
                }
            }
        }

        stage("Gather factsy z pluginu"){
            steps{
                dir('ansible'){
                    ansiblePlaybook(credentialsId: '$ansible_private_key', vaultCredentialsId: 'ansible_vault_key', inventory: 'inventory', playbook: 'tools_config.yml', colorized: true, limit: 'test')
                }
            }
        }
    }

    post{
        always{
            cleanWs()
        }
    }
}