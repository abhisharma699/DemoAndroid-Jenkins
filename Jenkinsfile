pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10', daysToKeepStr: '30'))
        //ansiColor('xterm')
        disableConcurrentBuilds()
    }
    triggers { 
      pollSCM('1/* * * * *') 
    }
   
        agent any
                stages {
            stage("Git checkout") {
                steps {
//                     script {
//                         properties([pipelineTriggers([pollSCM('H * * * *')])])
//                     }
                    git "https://github.com/deepforu47/DemoAndroid-Jenkins.git"
                }
            }
            stage("Unit tests") {
                steps{
                       
                        sh 'echo "Hello Unit Test Stage 1"'
                       
                }
            }
            // Build App
                stage('Build App') {
                    steps{
                            sh 'echo "Hello Build Stage again"'
                        
                    }
                }
            }
      }
