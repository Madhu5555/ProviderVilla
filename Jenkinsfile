pipeline {

                agent any

                stages {

                                stage('Source') {

                                                steps {

                                                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], gitTool: 'default', submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Madhu5555/ProviderVilla.git']]])

                                                }

                                }

                                stage('Build') {

                                                tools {

                                                                jdk 'jdk8'

                                                                maven 'maven'

                                                }

                                                steps {
                                                  dir('PV_Automation/') {
                                                   powershell 'mvn clean package'
                                                      }

                                                               

                                                               

                                                }

                                }

                               

                                stage('Code Quality') {

                   steps {

                                                                                script{

                                                                                                withSonarQubeEnv(installationName: 'SonarCube'){

                                                                                                powershell label: '', script: 'mvn sonar:sonar'

                         }

                       }

                                   }

                               

                                }

                                }

                                }
