pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                git ''
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying to production'
                // Your deployment steps go here
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
    }
}
