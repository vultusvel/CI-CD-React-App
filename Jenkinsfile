pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/vultusvel/CI-CD-React-App.git'
            }
        }

        stage('Install') {
            steps {
                sh 'npm ci'
            }
        }

        stage('Lint') {
            steps {
                sh 'npm run lint'
            }
        }

        stage('Test') {
            steps {
                sh 'npm run test'
            }
        }

        stage('Build') {
            steps {
                sh 'npm run build'
            }
        }

        stage('Deploy to Staging') {
            steps {
                sh 'echo Deploying to staging...'
            }
        }

        stage('Manual Deploy to Prod') {
            steps {
                input 'Deploy to production?'
                sh 'echo Deploying to production...'
            }
        }
    }
}
