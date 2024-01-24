pipeline {
    agent any

    environment {
        // Define environment variables if needed
        MAVEN_HOME = tool 'Maven'
        NEXUS_URL = 'http://http://18.191.170.217:8081/nexus'
        NEXUS_CREDENTIAL_ID = 'nexus-logins'

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from Git
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Set up Maven
                script {
                    def mvnHome = tool 'Maven'
                    def mavenCMD = "${mvnHome}/bin/mvn"

                    // Build the Maven project
                    sh "${mavenCMD} clean install"
                }
            }
        }

        stage('Deploy to Nexus') {
            steps {
                script {
                    def mvnHome = tool 'Maven'
                    def mavenCMD = "${mvnHome}/bin/mvn"

                    // Deploy the Maven artifacts to Nexus
                    sh "${mavenCMD} deploy -Dmaven.wagon.http.ssl.insecure=true -Dmaven.wagon.http.ssl.allowall=true"
                }
            }
        }
    }

    post {
        always {
            // Cleanup steps, if necessary
        }

        success {
            echo 'Build and deployment successful!'
        }

        failure {
            echo 'Build or deployment failed!'
        }
    }
}
