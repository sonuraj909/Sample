pipeline {
    agent any
    tools {
        flutter 'flutter-sdk'  // Use the Flutter installation you've configured in Jenkins
    }
    stages {
        stage('GIT PULL') {
            steps {
                git 'https://github.com/sonuraj909/Sample.git'
            }
        }
        stage('TEST') {
            steps {
                bat 'flutter test'  // Ensure Flutter is available in this context
            }
        }
        stage('BUILD') {
            steps {
                bat 'flutter build'  // Your build command
            }
        }
        stage('DISTRIBUTE') {
            steps {
                // Distribution steps
            }
        }
    }
}
