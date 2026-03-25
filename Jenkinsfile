pipeline {
    agent any

    environment {
        // Jenkins secret text credentials for Vercel
        VERCEL_TOKEN = credentials('vercel-token')
    }

    stages {
        stage('Install') {
            steps {
                // Install npm dependencies
                bat 'npm install'
            }
        }

        stage('Test') {
            steps {
                // Placeholder for tests
                echo 'No tests defined'
            }
        }

        stage('Build') {
            steps {
                // Build project (adjust if using React/Next.js)
                bat 'npm run build'
            }
        }

        stage('Deploy') {
            steps {
                // Use npx and pass token correctly for Windows CMD
                // %VERCEL_TOKEN% works in bat on Windows
                bat 'npx vercel --prod --confirm --token=%VERCEL_TOKEN%'
            }
        }
    }
}