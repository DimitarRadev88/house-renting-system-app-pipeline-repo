pipeline {

    agent any
    
    stages {
        stage('Checkout code') {
            steps {
            checkout scm
            }
        }

        stage('Restore dependencies') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build') {
            steps {
                bat 'dotnet build --no-restore'
            }
        }

        stage('Run tests') {
            steps {
                bat 'dotnet test --no-build --verbosity normal'
            }
        }

    }

    post {
        success {
           echo 'Build sucessfull'
        }

        failure {
            echo 'Pipeline failed!'
        }

        unstable {
            echo 'Tests failed'
        }

    }

}