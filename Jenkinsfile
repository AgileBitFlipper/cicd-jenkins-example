pipeline {

    agent any
    tools {
        maven 'Maven_3.5.2'
    }
    stages {

        stage ('Build') {

            steps {
                withMaven(maven: 'maven_3_5_2') {
                    sh 'mvn clean package'
                }
            }

        }

        stage ('Deploy') {

            steps {
                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'USERNAME',
                                  passwordVariable: 'PASSWORD']]) {
                    sh 'pks login -a cesicypksapi.cesi.cy -u andrew.montcrieff -u $USERNAME -k'
                    sh 'pks push'
                }
            }

        }
    }
}