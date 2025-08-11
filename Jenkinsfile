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
                sh 'mvn clean install --add-opens=jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED'
            }
                
        }
    }
}
