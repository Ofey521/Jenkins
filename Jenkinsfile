import groovy.io.FileType
@Library('shared-library') _

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
        stage("Pobranie zewnętrznej konfiguracji"){
            steps{
                script{
                    config()
                }
            }
        }
    }
    post{
        always{
            echo "========always========"
        }
    }
}