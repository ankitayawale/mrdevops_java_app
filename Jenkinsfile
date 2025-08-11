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
                sh '''
                    export MAVEN_OPTS="--add-opens=jdk.compiler/com.sun.tools.javac.processing=ALL-UNNAMED"
                    mvn clean install
                '''
            }
        }
    }
}

