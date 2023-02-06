import groovy.io.FileType

pipeline{
    agent{
        label 's08'
    }
    stages{
        stage("To jest step dla wersji 5.4"){
            steps{
                echo "5.4"
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
    }
}