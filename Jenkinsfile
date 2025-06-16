pipeline {
    agent any

    tools {
        nodejs 'Node18'  // Assure-toi que c’est bien écrit avec une majuscule : 'Node18'
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
                // Lance app.js dans une nouvelle fenêtre détachée grâce à start
                bat 'start "" node app.js'
            }
        }
    }
}
