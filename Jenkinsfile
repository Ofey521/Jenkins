pipeline{
    agent{
        label "ansible"
    }
    stages{
        stage("Sprawdź wersję ansibla"){
            steps{
                sh ''' 
                    ansible --version
                '''
            }
        }
        stage("A"){
            steps{
                dir('/home/ansible'){
                    sh '''
                        ansible linux -m gather_facts
                    '''
                }
            }

        }
    }

}