@Library('jenkins-helpers@java-8')_

pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                buildStep()
            }
        }
        stage('Document and Deploy') {
            // run this stage only when on master in the original repository
            when {
                environment name: 'CHANGE_FORK', value: ''
                expression { GIT_URL ==~ 'https://github.com/sw4j-org/.*' }
            }
            parallel {
                stage('Deploy') {
                    steps {
                        doDeploy()
                        publishSite()
                    }
                }
            }
        }
    }
}
