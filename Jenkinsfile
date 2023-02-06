import groovy.io.FileType

pipeline{
    agent{
        label 's08'
    }
    stages{
        stage("To jest step dla wersji 6.0"){
            steps{
                echo "6.0"
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