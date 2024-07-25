pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/sekharr606/task1.git'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building...'
                // Add your build steps here
                // For example, if you are using Maven:
                // sh 'mvn clean install'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                // Add your test steps here
                // For example, if you are using Maven:
                // sh 'mvn test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                // Add your deployment steps here
                // For example, if you are deploying to a server:
                // sh 'scp target/*.jar user@server:/path/to/deploy'
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
            // Add cleanup steps here
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
