pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Build') {
            steps {
                sh 'dotnet build'
            }
        }
        
        stage('Test') {
            steps {
                sh 'dotnet test'
            }
        }
        
        stage('Publish') {
            steps {
                sh 'dotnet publish -c Release -o ./publish'
            }
        }
    }
    
    post {
        failure {
            emailext (
                subject: "Pipeline Failed",
                body: "There was an error in the Jenkins pipeline. Please investigate.",
                to: "your.email@example.com"
            )
        }
    }
}
