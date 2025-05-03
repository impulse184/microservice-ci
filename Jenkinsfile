pipeline {
    agent any
    environment {
        ARTIFACTORY_URL = 'https://your-artifactory-instance'
        ARTIFACTORY_REPO = 'libs-release-local'
    }
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                script {
                    sh './gradlew build'
                }
            }
        }
        stage('Test') {
            steps {
                script {
                    sh './gradlew test'
                }
            }
        }
        stage('Publish Artifact') {
            steps {
                script {
                    // Upload to Artifactory
                    sh './gradlew uploadArchives'
                }
            }
        }
    }
}
