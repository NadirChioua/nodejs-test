pipeline {
    agent any

    tools {
        nodejs 'Node18'  // Assure-toi que ce nom correspond exactement dans Jenkins
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

        stage('Lancer l\'application localement') {
            steps {
                bat 'start "" node app.js'
            }
        }

        stage('Créer une image Docker') {
            steps {
                bat 'docker build -t nodejs-test-app .'
            }
        }

        stage('Lancer le conteneur Docker') {
            steps {
                bat 'docker run -d -p 3000:3000 nodejs-test-app'
            }
        }
    }
}
