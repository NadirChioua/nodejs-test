pipeline {
  agent any

  tools {
    nodejs 'Node18'   // ⚠️ Respecter exactement ce nom
  }

  stages {
    stage('Cloner le dépôt') {
      steps {
        // Cloner automatiquement le repo depuis GitHub
        checkout scm
      }
    }

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
        bat 'npm start'
        // ou bat 'node app.js' selon ton package.json
      }
    }
  }
}
