def gv
pipeline {
    agent any
    parameters {
        // string(name: 'VERSION', defaultValue: '', description: 'Version number on prod')
        choice(name: 'VERSION', choices: ['1.0', '1.1', '1.2'], description: 'Version number on prod')
        booleanParam(name: 'executeTests', defaultValue: true, description: 'Check to execute tests')
    }
    stages {
        stage("Init") {
            steps {
                script {
                    gv = load "script.groovy"
                }
            }
        }
        stage('Build') {
            steps {
                // Add your build steps here                
                // echo "Building the project"
                script {
                    gv.buildApp()
                }
            }
        }

        stage('Test') {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                // Add your test steps here
                // echo "Testing the project"
                script {
                    gv.testApp()
                }
            }
        }

        stage('Deploy') {
            steps {
                // Add your deployment steps here ok
                // echo "Deploying the project"
                // echo "Deploying version ${params.VERSION}"
                script {
                    gv.deployApp()
                }
            }
        }
    }

}
