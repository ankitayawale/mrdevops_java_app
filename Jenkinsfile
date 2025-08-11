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

        stage("Unit Test Maven") {
            steps {
               script{

                   mvnTest()
               }
                
            }
        }
    }
}
