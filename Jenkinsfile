pipeline{
    agent{
        label "ansible"
    }
    environment {
        ansible_private_key=credentials('ansible-priv')
        ofey=credentials('ofey_pass')
    }
    stages{
        stage("Sprawdź wersję ansibla"){
            steps{
                sh ''' 
                    ansible --version
                '''
            }
        }

        stage('Pull') {
            steps {
                dir('ansible'){
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']], userRemoteConfigs: [[credentialsId: 'ansible-priv' ,url: 'git@github.com:Ofey521/Ansible.git']]])
                }
            }
        }

        stage("Gather factsy"){
            steps{
                sh 'ansible -i /home/ansible --private-key=$ansible_private_key linux -m gather_facts'
            }
        }

        stage("Gather factsy z pluginu"){
            steps{
                ansiblePlaybook(credentialsId: '$ansible_private_key', inventory: '/home/ansible', playbook: '/home/ansible/ping.yml')
            }
        }
    }
}