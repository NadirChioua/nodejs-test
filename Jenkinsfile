pipeline {
    agent any

    tools {
        nodejs 'node18'
    }

    stages {
        stage('Install dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Start Application') {
            steps {
                bat 'npm start'
            }
        }
    }
}
