pipeline {
    agent any

    tools {
        nodejs 'Node18'  // nom exact dans Jenkins
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

        stage('Arrêter ancien conteneur (sécurisé)') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'UNSTABLE') {
                    bat '''
                    echo Suppression de l'ancien conteneur s’il existe...
                    docker stop nodejs-test-container || echo Aucun conteneur à arrêter
                    docker rm nodejs-test-container || echo Aucun conteneur à supprimer
                    '''
                }
            }
        }

        stage('Lancer le conteneur Docker') {
            steps {
                bat '''
                echo Lancement du conteneur nodejs-test-container...
                docker run -d -p 3000:3000 --name nodejs-test-container nodejs-test-app
                '''
            }
        }
    }
}
