pipeline {
    agent any
    environment {
        // You can directly specify the Flutter SDK path if it's installed on the system
        FLUTTER_HOME = 'C:/flutter'  // Set this path based on where Flutter is installed on your Jenkins server
    }
    stages {
        stage('GIT PULL') {
            steps {
                git 'https://github.com/sonuraj909/Sample.git'  // Pull the latest code from the repository
            }
        }
        stage('SETUP ENVIRONMENT') {
            steps {
                // Set the PATH to include Flutter SDK so the flutter command is available
                script {
                    def flutterBin = "${env.FLUTTER_HOME}/bin"
                    if (!fileExists("${flutterBin}/flutter")) {
                        error "Flutter SDK not found in the specified path."
                    }
                    env.PATH = "${flutterBin}:${env.PATH}"
                }
                bat 'flutter doctor'  // Ensure Flutter is installed correctly
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
