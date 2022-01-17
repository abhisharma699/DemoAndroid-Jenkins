pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10', daysToKeepStr: '30'))
        //ansiColor('xterm')
        disableConcurrentBuilds()
    }
    properties([pipelineTriggers([pollSCM('H * * * *')])])
        agent any
                stages {
            stage("Git checkout") {
                steps {
                    git "https://github.com/deepforu47/DemoAndroid-Jenkins.git"
                }
            }
            stage("Unit tests") {
                steps{
                       
                        sh 'echo "Hello Unit Test Stage"'
                       
                }
            }
            // Build App
                stage('Build App') {
                    steps{
                            sh 'echo "Hello Build Stage'
                        
                    }
                }
            }
      }

