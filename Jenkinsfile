pipeline {
    agent any

    environment {
        VERCEL_TOKEN = credentials('vercel-token')
    }

    stages {
        stage('Restore & Build .NET') {
            steps {
                echo 'Restoring and building .NET project...'
                bat 'dotnet restore WebApplication3.sln'
                bat 'dotnet build WebApplication3.sln -c Release'
            }
        }

        stage('Publish .NET') {
            steps {
                echo 'Publishing .NET project...'
                bat 'dotnet publish WebApplication3.sln -c Release -o publish'
            }
        }

        stage('Deploy Frontend to Vercel') {
            steps {
                echo 'Deploying frontend to Vercel...'
                // Only deploy the wwwroot folder inside publish
                bat 'npx vercel publish publish/wwwroot --prod --confirm --token=%VERCEL_TOKEN%'
            }
        }
    }
}