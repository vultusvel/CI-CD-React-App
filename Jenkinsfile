pipeline {
    agent any
    
    environment {
        NODE_ENV = 'development'
    }

    stages {
        stage('Check Docker') {
            steps {
                sh 'docker --version'
            }
        }

        stage('Install dependencies') {
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
            when {
                branch 'main'
            }
            steps {
                echo 'Deploying to staging...'
            }
        }

        stage('Manual Prod Deploy') {
            when {
                branch 'main'
            }
            steps {
                input message: 'Deploy to PROD?', ok: 'Deploy'
                sh 'vercel --prod' 
            }
        }
    }
}
