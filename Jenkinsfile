pipeline {
    agent any

    tools {
        nodejs 'Node18' // Assure-toi que ce nom correspond à celui dans Jenkins > Tools
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

        stage('Créer une image Docker') {
            steps {
                bat 'docker build -t nodejs-test-app .'
            }
        }

        stage('Arrêter anciens conteneurs (optionnel)') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
                    bat '''
                    echo Arrêt des conteneurs existants...
                    for /F %%i in ('docker ps -a -q --filter "ancestor=nodejs-test-app"') do (
                        docker stop %%i || echo Aucun à arrêter
                        docker rm %%i   || echo Aucun à supprimer
                    )
                    '''
                }
            }
        }

        stage('Lancer le conteneur Docker') {
            steps {
                bat 'docker run -d -p 3000:3000 nodejs-test-app'
                bat 'docker ps'
            }
        }
    }
}
