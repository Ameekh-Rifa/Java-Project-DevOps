@Library ('Jenkins-shared-library') _

pipeline {
    agent any 
        stages {
            stage ("Git checkout") {
                steps {
                    script {
                        gitCheckout {
                            branch: 'main'
                            credentialsId: 'PAT_Git_Jenkins'
                            url: 'https://github.com/Ameekh-Rifa/Java-Project-DevOps.git'
                        }
                    }
                }
            }
        }
}