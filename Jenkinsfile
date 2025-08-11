@Library('my-shared-library') _

pipeline {
    agent any

    stages {
        stage("Git Checkout") {
            steps {
                script {
                    gitCheckout(
                        branch: "main",
                        url: "https://github.com/ankitayawale/mrdevops_java_app.git"
                    )
                }
            }
        }

        stage("Build with Maven") {
            steps {
                script{
                    mvnTest()
                }
        
            }
        }

        stage("Integration test Maven") {
            steps {
                script{
                    mvnIntegrationTest()
                }
                
            }
        }
    }
}

