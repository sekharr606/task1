pipeline {
    agent any

    environment {
        NODE_HOME = '/usr/local/bin' // Path to your Node.js installation
        GIT_CREDENTIALS_ID = 'your-git-credentials-id'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://gitlab.com/iac2312807/task1.git', credentialsId: env.GIT_CREDENTIALS_ID
            }
        }

        stage('Install Dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run Tests') {
            steps {
                sh 'npm test'
            }
        }

        stage('Deploy') {
            steps {
                sh 'npm start &'
            }
        }
    }

    post {
        always {
            // Actions that always run after the pipeline completes
            echo 'Cleaning up...'
            deleteDir()
        }
        success {
            echo 'Pipeline completed successfully!'
        }
        failure {
            echo 'Pi
