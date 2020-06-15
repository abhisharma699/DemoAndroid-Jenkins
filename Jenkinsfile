pipeline {
           agent any
           stages {
                // stage("Git checkout") {
                //      steps {
                //           git "https://github.com/Ritvikjain/DemoAndroid.git"
                //      }
                // }
                stage("Unit tests") {
                    steps{
                        bat 'gradlew clean test'
                    }
                }
                stage("Static Code Analysis") {
                    steps{
                        bat 'gradlew clean lint'
                    }
                            post {
                always {
                    androidLint canComputeNew: false, defaultEncoding: '', healthy: '', pattern: 'app/build/reports/lint-results.xml', unHealthy: ''
                }
            }
                }
                stage("Build") {
                    steps {
                        bat 'gradlew clean build -x test -x lint'
                    }
                }
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
                }*/
           }
      }

