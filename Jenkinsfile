pipeline {
    agent any

    tools {
        nodejs "node18"
    }

    stages {
        stage('Install dependencies') {
            steps {
                bat 'npm install'
            }
        }

        stage('Run tests') {
            steps {
                bat 'npm test'
            }
        }
    }
}
