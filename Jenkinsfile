import groovy.io.FileType
@Library('shared-library') _

pipeline{
    agent{
        label 's08'
    }
    stages{
        stage("To jest step dla wersji 5.5"){
            steps{
                echo "5.5"
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