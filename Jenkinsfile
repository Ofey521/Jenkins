pipeline{
    agent{
        label "s08"
    }
    stages{
        stage("Sprawdź co jest w folderze"){
            steps{
                dir("/mnt/db"){
                    sh "ls -lh"
                }
            }
            post{
                always{
                    echo "========always========"
                }
                success{
                    echo "========A executed successfully========"
                }
                failure{
                    echo "========A execution failed========"
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
        success{
            echo "========pipeline executed successfully ========"
        }
        failure{
            echo "========pipeline execution failed========"
        }
    }
}