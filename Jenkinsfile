pipeline {
    agent any

    environment {
        // Define environment variables
        DEPLOY_SERVER = '20.121.117.101'
        DEPLOY_USER = 'azureuser'
        DEPLOY_PATH = '/home/azureuser'
        APP_NAME = 'hello.js'
    }

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main', url: 'https://github.com/sekharr606/task1.git'
            }
        }
        
        stage('Build') {
            steps {
                echo 'Building...'
                dir('project') { // Ensure this path is correct
                    sh 'mvn clean install'
                }
            }
        }

        stage('Test') {
            steps {
                echo 'Testing...'
                dir('project') { // Ensure this path is correct
                    sh 'mvn test'
                }
            }
        }

        stage('Package') {
            steps {
                echo 'Packaging...'
                dir('project') { // Ensure this path is correct
                    sh 'mvn package'
                }
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying...'
                sh """
                scp project/target/${APP_NAME} ${DEPLOY_USER}@${DEPLOY_SERVER}:${DEPLOY_PATH}
                ssh ${DEPLOY_USER}@${DEPLOY_SERVER} 'cd ${DEPLOY_PATH} && ./restart-your-application.sh'
                """
            }
        }
    }

    post {
        always {
            echo 'Cleaning up...'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
