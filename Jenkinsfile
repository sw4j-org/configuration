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
                                mavenLocalRepo: '${JENKINS_HOME}/maven-repositories/${EXECUTOR_NUMBER}/',
                                globalMavenSettingsConfig: '9a4daf6d-06dd-434a-83cc-9ba9bd2326fc') {
                            sh "mvn deploy"
                        }
                    }
                }
                stage('Create Site') {
                    steps {
                        withMaven(jdk: 'Current JDK 8',
                                maven: 'Current Maven 3',
                                mavenLocalRepo: '${JENKINS_HOME}/maven-repositories/${EXECUTOR_NUMBER}/') {
                            sh "mvn -Dscmpublish.skipCheckin=true post-site scm-publish:publish-scm"
                        }
                        withCredentials([string(credentialsId: "f9c0bd13-de91-4d90-a292-8fd2d05c26b0", variable: 'GH_TOKEN')]) {
                            sh """
                                cd target/scmpublish-checkout
                                git commit -a -m 'Automatic created documentation'
                                git push -fq https://${GH_TOKEN}@github.com/sw4j-org/quality-profile.git gh-pages:gh-pages
                            """
                        }
                    }
                }
            }
        }
    }
}