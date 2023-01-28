pipeline{
    agent{
        label "ansible"
    }

    parameters{
        string(name: "INVENTORY", defaultValue: "", description: "Którą grupę inventory chcesz zaktualizować?")
    }

    environment {
        ansible_private_key=credentials('ansible-priv')
    }
    
    stages{
        stage('Pull') {
            steps {
                dir('ansible'){
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'ansible-priv' ,url: 'git@github.com:Ofey521/Ansible.git']]])
                }
            }
        }

        stage("tools config"){
            steps{
                dir('ansible'){
                    ansiblePlaybook(credentialsId: '$ansible_private_key', vaultCredentialsId: 'ansible_vault_key', inventory: 'inventory', playbook: 'tools_config.yml', colorized: true, limit: params.INVENTORY)
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