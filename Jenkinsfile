pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                // Check out code from the repository
                checkout scm
            }
        }
        stage('Build') {
            steps {
                // Build your application here
                sh 'mvn clean install'
            }
        }
        stage('Deploy') {
            steps {
                // Deploy your application here
                sh './deploy.sh'
            }
        }
    }
}
