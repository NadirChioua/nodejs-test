pipeline {
    agent any

    tools {
        nodejs 'Node18'  // Assure-toi que ce nom est bien défini dans Jenkins > Global Tool Configuration
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
                bat '''
                    echo Vérification des conteneurs existants basés sur l'image...
                    FOR /F "tokens=*" %%i IN ('docker ps -q --filter "ancestor=nodejs-test-app"') DO docker stop %%i
                    echo Lancement d'un nouveau conteneur Docker...
                    docker run -d -p 3000:3000 nodejs-test-app
                '''
            }
        }
    }
}
