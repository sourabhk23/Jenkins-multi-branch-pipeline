pipeline {
    agent any
    environment {
        DEPLOY_ENV = ''
    }
    stages {
        stage('Build') {
            steps {
                // Your build commands go here
                echo 'Building the application...'
            }
        }

        stage('Test') {
            steps {
                // Test the application
                echo 'Running tests...'
            }
        }

        stage('Deploy to QA') {
            when {
                branch 'qa'
            }
            steps {
                script {
                    DEPLOY_ENV = 'qa'
                }
                // Deployment to QA server
                echo 'Deploying to QA environment...'
                // Add your deploy command here, e.g., SSH or any deployment script
            }
        }

        stage('Deploy to UAT') {
            when {
                branch 'uat'
            }
            steps {
                script {
                    DEPLOY_ENV = 'uat'
                }
                // Deployment to UAT server
                echo 'Deploying to UAT environment...'
                // Add your deploy command here
            }
        }

        stage('Deploy to Production') {
            when {
                branch 'production'
            }
            steps {
                script {
                    DEPLOY_ENV = 'production'
                }
                // Deployment to Production server
                echo 'Deploying to Production environment...'
                // Add your deploy command here
            }
        }
    }
    post {
        always {
            echo "Deployment completed for $DEPLOY_ENV."
        }
    }
}

