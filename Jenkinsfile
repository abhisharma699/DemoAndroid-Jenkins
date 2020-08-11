pipeline {
    options {
        buildDiscarder(logRotator(numToKeepStr: '10', artifactNumToKeepStr: '10', daysToKeepStr: '30'))
        //ansiColor('xterm')
        disableConcurrentBuilds()
    }
           agent any
           stages {
             stage("Git checkout") {
                  steps {
                      git "https://github.com/deepforu47/DemoAndroid-Jenkins.git"
                  }
             }
                stage("Unit tests") {
                    steps{
                            //sh 'chmod +x gradlew'
                            //sh './gradlew clean test'
                            sh 'set +x && /usr/local/bin/fastlane clear"'
                            //bat 'gradlew testDebugUnitTest'
                    }
                    post{
                        always{
                                    junit 'app/build/test-results/testDebugUnitTest/*.xml'
                        }
                    }
                }
                stage("Static Code Analysis") {
                    steps{
                            sh './gradlew clean lint'
                    }
                    post {
                        always {
                            androidLint canComputeNew: false, defaultEncoding: '', healthy: '', pattern: 'app/build/reports/lint-results.xml', unHealthy: ''
                        }
                    }
                }
/*                stage("Build") {
                    steps {
                        sh './gradlew clean build -x test -x lint'
                    }
                } */
		// Build App
            stage('Build App') {
                steps{
                        script {
                            sh 'set +x && /usr/local/bin/fastlane build build_number:"${BUILD_NUMBER}"'
                        }
                    
                }
            }
// stage('SonarQube analysis') {
//             steps {
//                 script {
//                     scannerHome = tool 'sonarqube';
//                 }
//                 withSonarQubeEnv('sonarqube') { // If you have configured more than one global server connection, you can specify its name
//                     sh "./gradlew sonarqube -Dsonar.projectKey=android-demo-app"
//                 }
//             }
//         }
//         stage('Quality Gate') {
//             steps {
//                 timeout(time: 1, unit: 'HOURS') {
//                     // Parameter indicates whether to set pipeline to UNSTABLE if Quality Gate fails
//                     // true = set pipeline to UNSTABLE, false = don't
//                     waitForQualityGate abortPipeline: true
//                 }
//             }
//         }


                /*stage('Security Analysis') {
                    steps{
                        appscan application: '75d946aa-1f67-4f74-a4c3-dc9e9341d28f', 
                        credentials: 'HCL APP Center api', 
                        name: 'Adnroid Security', 
                        scanner: mobile_analyzer(hasOptions: false, target: 'C:/Program Files (x86)/Jenkins/workspace/AndroidProject/app/build/outputs/apk/debug/app-debug.apk'), 
                        type: 'Mobile Analyzer', 
                        wait: true
                    }
                }

                stage('Publish to App Center') {
                    environment {
                        APPCENTER_API_TOKEN = '553f659a621e5fa1dcdfecb8132bc60ee8ae3ce8'
                    }
                    steps {
                        appCenter apiToken: APPCENTER_API_TOKEN, 
                        appName: 'android-demo',
                        distributionGroups: 'Collaborators, testers', 
                        ownerName: 'ritjain2', 
                        pathToApp: 'app/build/outputs/apk/debug/app-debug.apk'
                    }
                } */
                stage('Appcenter Upload') {
                    steps{
                        dir('DemoAndroid-Jenkins'){
                            sh '/usr/local/bin/fastlane upload_to_appcenter scm_change:"$(git log -5 HEAD --no-merges --pretty=format:%s)"'
                    
                        }
                    }
                } 
           }
      }

