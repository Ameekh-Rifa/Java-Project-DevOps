@Library ('Jenkins-shared-library') _

pipeline {
    agent any 
        stages {
            stage('Git Checkout'){
                steps{
                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/Ameekh-Rifa/Java-Project-DevOps.git"
                        )
                     }
            }
            stage('Maven Unit test') {
                steps {
                    script {
                        mvnTest()
                    }
                }
            }
            stage('Maven Integration Testing') {
                steps {
                    script {
                        mvnIntegrationTest()
                    }
                }
            }
        }
    }
