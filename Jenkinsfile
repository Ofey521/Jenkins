import groovy.io.FileType
@Library('shared-library') _

pipeline{
    agent{
        label 's08'
    }
    parameters {
        string(name: 'path', description: 'path to database')
        string(name: 'ver', description: 'version of program')
    }
    stages{
        stage("To jest step dla wersji 5.4"){
            steps{
                echo "5.4"
                echo "${params.ver}"
                echo "${params.path}"
            }
        }
        stage("Pobranie zewnętrznej konfiguracji"){
            steps{
                script{
                    def result = config(path: "${params.path}", version: "${params.ver}")
                    path = "${result.path}"
                    ver = "${result.version}"
                }
            }
        }
        stage("Poka parametry"){
            steps{
                script{
                    echo "${path}"
                    echo "${ver}"
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