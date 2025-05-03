
pipeline {
    agent any

    environment {
        // Optional: Define environment variables if needed
        BUILD_ENV = 'development'
    }

    stages {
        stage('Checkout') {
            steps {
                // Automatically checks out the current branch
                checkout scm
            }
        }

        stage('Build') {
            steps {
                echo 'Building the project...'
                sh './gradlew clean build'
            }
        }

        stage('Test') {
            steps {
                echo 'Running tests...'
                sh './gradlew test'
            }
        }

        stage('Archive Artifacts') {
            steps {
                echo 'Archiving JAR files...'
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build and tests succeeded.'
        }
        failure {
            echo 'Build or tests failed.'
        }
    }
}
