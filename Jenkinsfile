import groovy.io.FileType
@Library('shared-library') _

pipeline{
    agent{
        label 's07'
    }
    parameters {
        string(name: 'path', description: 'path to database')
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
                echo "${params.path}"
            }
        }
        stage("Pobranie zewnętrznej konfiguracji"){
            steps{
                script{
                    def result = config(path: "${params.path}", version: "${params.ver}", nVersion: "${params.nVersion}")
                    path = "${result.path}"
                    ver = "${result.version}"
                    nVersion = "${result.nVersion}"
                    if(nVersion == null) error 'nVersion not found in jenkins_env_conf'
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