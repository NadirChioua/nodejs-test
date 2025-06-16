pipeline {
    agent any

    tools {
        nodejs 'Node18'  // Attention à bien respecter la casse exacte : 'Node18'
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
                // Lance l'application sans bloquer Jenkins et redirige la sortie dans un fichier log
                bat 'node app.js > output.log 2>&1 &'
            }
        }
    }
}
