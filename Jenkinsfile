pipeline {
    agent {
        docker {
            image 'node:22-alpine'
        }
    }

    environment {
        FIREBASE_DEPLOY_TOKEN = credentials('firebase-token')
    }

    stages {
        stage('Building') {
            steps {
                sh 'npm install -g firebase-tools'
            }
        }

        stage('Testing') {
            steps {
                echo 'This is testing'
            }
        }

        stage('Staging') {
            steps {
                sh 'firebase deploy -P password-generator-staging --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }

        stage('Production') {
            steps {
                sh 'firebase deploy -P password-generator-production --token "$FIREBASE_DEPLOY_TOKEN"'
            }
        }
    }
}
