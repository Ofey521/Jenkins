import groovy.io.FileType

pipeline{
    agent{
        label 's08'
    }
    stages{
        stage("Sprawdź co jest w folderze"){
            agent { label 's08' }
            steps{
                script {
                    //sh "if [ -d /mnt/db ]; then ls /mnt/db; fi > commandResult"
                    sh "ls /mnt/db > list_database "
                    result = readFile('list_database').trim()
                    println result
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