import groovy.io.FileType
@Library('shared-library') _

pipeline{
    agent{
        label 's07'
    }
    parameters {
        string(name: 'ver', description: 'version of program')
        string(name: 'nVersion', description: 'nVersion', trim: true)
    }
    environment{
        nVersion = "-"
    }
    stages{
        stage("To jest step dla wersji 5.4"){
            steps{
                echo "5.4"
                echo "${params.ver}"
            }
        }
        stage("Pobranie zewnętrznej konfiguracji"){
            steps{
                script{
                    def result = config(version: "${params.ver}", nVersion: "${params.nVersion}")
                    path = "${result.path}"
                    ver = "${result.version}"
                    nVersion = "${result.nVersion}"
                }
            }
        }
        stage("Poka parametry"){
            steps{
                script{
                    echo "${path}"
                    echo "${ver}"
                    echo "${nVersion}"
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