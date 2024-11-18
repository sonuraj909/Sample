pipeline {
    agent any
    tools {
        flutter 'flutter-sdk'  // Ensure Flutter SDK is configured in Jenkins global tools
    }
    environment {
        // Set the Flutter SDK version (based on your environment setup)
        FLUTTER_VERSION = '^3.5.1'
    }
    stages {
        stage('GIT PULL') {
            steps {
                git 'https://github.com/sonuraj909/Sample.git'  // Pull the latest code from the repository
            }
        }
        stage('SETUP ENVIRONMENT') {
            steps {
                // You can run commands to install specific dependencies based on version or perform any environment setup
                bat 'flutter doctor'  // Check Flutter setup
                bat 'flutter pub get'  // Install dependencies based on pubspec.yaml
            }
        }
        stage('TEST') {
            steps {
                bat 'flutter test'  // Run tests using Flutter framework
            }
        }
        stage('BUILD') {
            steps {
                bat 'flutter build'  // Build your Flutter app (adjust this as per your build target, i.e., APK, iOS, etc.)
            }
        }
        stage('DISTRIBUTE') {
            steps {
                // If you have specific deployment steps, you can add them here.
                echo 'Distribution steps go here.'
                // Example: bat './deploy.bat'  // Use a deployment script if necessary.
            }
        }
    }
}
