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
                    configData = readYaml file: "jenkins_env_conf.yml"
                    path = configData.path
                    echo "$path"
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