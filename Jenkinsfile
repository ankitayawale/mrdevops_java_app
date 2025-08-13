@Library('my-shared-library') _

pipeline {

    agent any

    parameters{
        choice(name: 'action', choices: 'create\ndelete', description: 'Select an action')
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

        stage("Sonarqube test analysis: Sonarqube") {

            when { expression { params.action == 'create'} }
            
            steps {
                script{

                    def SonarQubecredentialsId= 'sonarqube-api'
                    statiCodeAnalysis(SonarQubecredentialsId)
                }
                
            }
        }

        stage("Quality Gate Status Check: Sonarqube") {

            when { expression { params.action == 'create'} }
            
            steps {
                script{

                    def SonarQubecredentialsId= 'sonarqube-api'
                    QualityGateStatus(SonarQubecredentialsId)
                }
                
            }
        }

         stage("Maven Build: maven") {

            when { expression { params.action == 'create'} }
            
            steps {
                script{

                    mvnBuild()
                }
                
            }
        }

        stage("Docker Image Build: maven") {

            when { expression { params.action == 'create'} }
            
            steps {
                script{

                    mvnBuild()
                }
                
            }
        }
    }
}

