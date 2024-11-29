pipeline {
    agent any

    environment {
        REPO_URL = 'https://github.com/Ahmed10911/microservice-app.git'
    }

    stages {
        stage('Checkout') {
            steps {
                // Cloning the private repository
                git branch: 'main', credentialsId: 'github-pat-2', url: "${REPO_URL}"
            }
        }
        stage('Build') {
            steps {
                // Building the microservice
                sh 'mvn clean install'
            }
        }
        stage('Test') {
            steps {
                // Running tests
                sh 'mvn test'
            }
        }
        stage('Package') {
            steps {
                // Packaging the application
                sh 'mvn package'
            }
        }
    }
    post {
        success {
            // Notify on successful build
            echo 'Build Successful'
        }
        failure {
            // Notify on failure
            echo 'Build Failed'
        }
    }
}
