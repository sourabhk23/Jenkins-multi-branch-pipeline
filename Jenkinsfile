pipeline {
    agent any
    environment {
        DEPLOY_ENV = ''
    }
    stages {
        stage('Build') {
            steps {

                echo 'Building the application...'
            }
        }

        stage('Test') {
            steps {

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
                echo 'Deploying to QA environment...'


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

                echo 'Deploying to UAT environment...'

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

                echo 'Deploying to Production environment...'

            }
        }
    }
    post {
        always {
            echo "Deployment completed for $DEPLOY_ENV."
        }
    }
}

