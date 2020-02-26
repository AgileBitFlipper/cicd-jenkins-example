pipeline {

    // Run on any executor.
    agent any

    // How do we interact with kubernetes to utillize
    //   an agent?

    // Docker executor  
    // agent {
    //     docker {
    //         image 'maven:3-alpine'
    //         args '-v /root/.m2:/root/.m2'
    //     }
    // }

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

            // Deploy with PKS
            
            // steps {
                // withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                //                   credentialsId   : 'PCF_LOGIN',
                //                   usernameVariable: 'USERNAME',
                //                   passwordVariable: 'PASSWORD']]) {
                //     sh 'pks login -a cesicypksapi.cesi.cy -u andrew.montcrieff -u $USERNAME -k'
                //     sh 'pks push'
                // }
            // }

        }
    }
}