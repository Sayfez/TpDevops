pipeline {
    agent any

    stages {
        stage('git') {
            steps {
                // Cloner le référentiel depuis votre système de contrôle de version
                 url: https://github.com/Sayfez/TpDevops  
                  }
        }
        /*stage('Construction') {
            steps {
                // Exécuter votre processus de construction (par exemple, Maven, Gradle, etc.)
                 'mvn clean install'
            }
        }
        stage('Tests') {
            steps {
                // Exécuter vos tests unitaires ou tests d'intégration
                 'mvn test'
            }
        }
        stage('Déploiement') {
            steps {
                // Déployer votre application sur un serveur ou une plateforme spécifique
                 'mvn deploy'
            }
        }*/
    }
}
