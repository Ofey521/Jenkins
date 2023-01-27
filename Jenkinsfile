pipeline{
    agent{
        label "ansible"
    }
    environment {
        ansible_private_key=credentials('ansible-priv')
    }
    stages{
        stage("Sprawdź wersję ansibla"){
            steps{
                sh ''' 
                    ansible --version
                '''
            }
        }
        stage("Gather factsy"){
            steps{
                sh 'ansible -i /home/ansible --private-key=$ansible_private_key linux -m gather_facts'
            }

        }
    }
}