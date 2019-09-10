pipeline {

    agent any

    stages {

        stage ('Build') {
            steps {
                withMaven(maven: 'maven_3_5_0') {
                    sh 'mvn clean package'
                }
            }
        }

        stage ('Deploy') {
            steps {

                withCredentials([[$class          : 'UsernamePasswordMultiBinding',
                                  credentialsId   : 'PCF_LOGIN',
                                  usernameVariable: 'bharatkumar353@gmail.com',
                                  passwordVariable: 'Richa@100']]) {

                    sh '/usr/local/bin/cf login -a http://api.run.pivotal.io -u bharatkumar353@gmail.com -p Richa@100'
                    sh '/usr/local/bin/cf push'
                }
            }

        }

    }

}