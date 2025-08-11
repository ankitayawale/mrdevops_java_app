@Library('my-shared-library') _

pipeline {

    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', choose: 'choose create/destroy')
    }

    stages {

        when { expression { param.action == 'create'} }
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

            when { expression { param.action == 'create'} }

            steps {
                script{
                    mvnTest()
                }
        
            }
        }

        stage("Integration test Maven") {

            when { expression { param.action == 'create'} }

            steps {
                script{
                    mvnIntegrationTest()
                }
                
            }
        }

        stage("Sonarqube test analysis: Sonaeqube") {

            when { expression { param.action == 'create'} }
            
            steps {
                script{
                    statiCodeAnalysis()
                }
                
            }
        }
    }
}

