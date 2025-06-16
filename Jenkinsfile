pipeline {
    agent any

    tools {
        nodejs 'Node18'
    }

    stages {
        stage('Check environnement') {
            steps {
                bat 'echo Environnement Windows détecté'
            }
        }

        stage('Installer les dépendances') {
            steps {
                bat 'npm install'
            }
        }

        stage('Lancer l\'application') {
            steps {
                bat 'start /B node app.js & timeout /T 5'
            }
        }
    }
}
