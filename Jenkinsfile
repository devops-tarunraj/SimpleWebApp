pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the GitHub repository
                git 'https://github.com/devops-tarunraj/SimpleWebApp.git'
            }
        }
        stage('Build') {
            steps {
                // Use the configured Maven installation to build the project
                withMaven(maven: 'maven') {
                    sh 'mvn clean package' // Execute Maven command to build the project and package it into a JAR file
                }
            }
        }
    }
}
