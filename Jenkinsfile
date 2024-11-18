pipeline {
    agent any

    stages {
        stage('GIT PULL') {
            steps {
                git branch: "main", url: 'https://github.com/sonuraj909/Sample.git'
            }
        }
        stage('TEST') {
            steps {
                sh 'flutter test'
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
                        pathToApp: ' build\app\outputs\flutter-apk\app-release.apk',
                        distributionGroups: 'AlphaTester'
            }
        }
    }
}