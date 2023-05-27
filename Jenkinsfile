@Library ('Jenkins-shared-library') _

pipeline 
    {
    agent any 
        parameters {
            choice(name: 'action', choices: 'create\ndelete', description: 'Create/Destroy')
        }
        stages {
            stage('Git Checkout'){
                when { expression { params.action == 'create' } }
                steps{
                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/Ameekh-Rifa/Java-Project-DevOps.git"
                        )
                     }
            }
            stage('Maven Unit test') {
                when { expression { params.action == 'create' } }
                steps {
                    script {
                        mvnTest()
                    }
                }
            }
            stage('Maven Integration Testing') {
                when { expression { params.action == 'create' } }
                steps {
                    script {
                        mvnIntegrationTest()
                    }
                }
            }
            stage('static code analysis'){
                when { expression { params.action == 'create' } }
                steps {
                    script {
                        def SonarQubecredentialsId = 'Sonar-Jenkins-Token'
                        staticCodeAnalysis(SonarQubecredentialsId)
                    }
                }
            }
            stage('Quality Gate status Check'){
                when { expression { params.action == 'create' } }
                steps {
                    script {
                        def SonarQubecredentialsId = 'Sonar-Jenkins-Token'
                        QualityGateStatus(SonarQubecredentialsId)
                    }
                }
            }
            stage('Maven Build'){
                when { expression { params.action == 'create' } }
                steps {
                    script {
                        mvnBuild()
                    }
                }
            }
        }
    }
