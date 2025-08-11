@Library('my-shared-library') _

pipeline {

    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'choose create/destroy')
    }

    stages {

        
        stage("Git Checkout") {
            when { 
                expression { params.action == 'create'}
            }
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
           when {
               expression { params.action == 'create'} 
           }

            steps {
                script{
                    mvnTest()
                }
        
            }
        }

        stage("Integration test Maven") {
           when { 
               expression { params.action == 'create'} 
           }

            steps {
                script{
                    mvnIntegrationTest()
                }
                
            }
        }

        stage("Sonarqube test analysis: Sonaeqube") {

            when { expression { params.action == 'create'} }
            
            steps {
                script{
                    statiCodeAnalysis()
                }
                
            }
        }
    }
}

