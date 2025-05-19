pipeline {
    agent {
        node {
            label 'agent-1'
    }
    }
    // environment {
    //         packageVersion = '' 
    //         nexusURL = '172.31.84.49:8081'
    //      }
    options {
        timeout(time: 1, unit: 'HOURS')
        disableConcurrentBuilds()
    }
    parameters {
        string(name: 'version', defaultValue: '1.0.0', description: 'What is the artifact version?')
        string(name: 'environment', defaultValue: 'dev', description: 'What is the environment?')
           }
    //build
    stages {
        stage('Deploy') {
            steps {
                sh """
                    echo "version: ${params.version}"
                    echo "environment: ${params.environment}"
                """
                }
            }
        }
    }
    //psot build
      post { 
        always { 
            echo 'I will always say Hello again!'
            deleteDir()        
        }
        failure{
            echo 'this runs when pipeline is failed, used generally to send some alerts'
        }
        success{
            echo 'I will say Hello, when pipeline is success'
        }
    }
}
