pipeline {
    agent any

    tools {
        Nodejs "node18"  // ✔️ Respect exact du nom
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
