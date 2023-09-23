pipeline {
    agent any
    triggers {
        //githubPush()
        githubPush branches: "develop"
    }
    stages {
        stage('Checkout') {
            steps {
                // Check out code from the repository
                checkout scm
            }
        }
        stage('Copy Files') {
            steps {
                // Run the deploy.sh script to copy files
                sh '/var/myscripts/deploy.sh'
            }
        }
    }
    post {
    success {
        // Set up a GitHub webhook for your repository
        script {
            try {
                def webhookUrl = 'http://100.26.41.139:8080/github-webhook/' // Replace with your Jenkins webhook URL
                def githubRepo = 'https://github.com/vpaturkar/git-assignment-5.git' // Replace with your GitHub repository URL

                // Create a GitHub webhook
                createWebhook(url: webhookUrl, projectFullName: githubRepo)
            } catch (Exception e) {
                currentBuild.result = 'FAILURE'
                error("Failed to create GitHub webhook: ${e.message}")
            }
        }
    }
}
}
