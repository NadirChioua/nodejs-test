pipeline {
    agent any

    tools {
        nodejs 'Node18'  // Nom défini dans Jenkins > Global Tool Configuration
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

        stage('Stopper & Supprimer anciens conteneurs Docker') {
            steps {
                bat '''
                    echo Arrêt et suppression des anciens conteneurs basés sur nodejs-test-app...
                    FOR /F "tokens=*" %%i IN ('docker ps -a -q --filter "ancestor=nodejs-test-app"') DO (
                        docker stop %%i
                        docker rm %%i
                    )
                '''
            }
        }

        stage('Lancer un nouveau conteneur Docker') {
            steps {
                bat 'docker run -d -p 3000:3000 nodejs-test-app'
            }
        }
    }
}
