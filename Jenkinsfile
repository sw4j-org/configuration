pipeline {
    agent any
    stages {
        stage('Checkout') {
            checkout scm
        }
        stage('Build') {
            steps {
                withMaven(jdk: 'Current JDK 8',
                        maven: 'Current Maven 3',
                        mavenLocalRepo: '${JENKINS_HOME}/maven-repositories/${EXECUTOR_NUMBER}/') {
                    sh "mvn clean install"
                }
            }
        }
        stage('Document and Deploy') {
            when {
                environment name: 'CHANGE_FORK', value: ''
                expression { GIT_URL ==~ 'https://github.com/sw4j-org/.*' }
            }
            parallel {
                stage('Deploy') {
                    steps {
                        withMaven(jdk: 'Current JDK 8',
                                maven: 'Current Maven 3',
                                mavenLocalRepo: '${JENKINS_HOME}/maven-repositories/${EXECUTOR_NUMBER}/') {
                            sh "mvn deploy"
                        }
                    }
                }
            }
        }
    }
}