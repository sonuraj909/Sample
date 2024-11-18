pipeline {
    agent any
 environment {
        PATH = "C:\\flutter_windows_3.24.1-stable\\flutter\\bin;${env.PATH}"
    }

    stages {
        stage('GIT PULL') {
            steps {
                git branch: "main", url: 'https://github.com/sonuraj909/Sample.git'
            }
        }
        stage('Flutter Doctor') {
    steps {
        bat 'flutter doctor'
    }
}


        stage('TEST') {
            steps {
                bat  'flutter test'
            }
        }
        stage('BUILD') {
            steps {
                sh '''
                  #!/bin/sh
                  flutter build apk --release
                '''
            }
        }
        stage('DISTRIBUTE') {
            steps {
                appCenter apiToken: 'ee64cfc12d27630d8d2fdc03ad631b75e61fea86',
                        ownerName: 'sonuraj909',
                        appName: 'Sample',
                        pathToApp: 'build/app/outputs/flutter-apk/app-release.apk', // Corrected path
                        distributionGroups: 'AlphaTester'
            }
        }
    }
}
