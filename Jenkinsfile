import groovy.io.FileType
@Library('shared-library') _

pipeline{
    agent{
        label 's08'
    }
    parameters {
        string(name: 'path', description: 'path to database')
        string(name: 'version', description: 'version of program')
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
                    config(path: "/home/sente")
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