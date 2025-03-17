pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git 'https://github.com/Tp3/productapp.git'
            }
        }
        
        stage('Build') {
            steps {
                sh './gradlew clean package'
            }
        }

        stage('Test') {
            steps {
                sh './gradlew test'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Déploiement en cours...'
            }
        }
    }
}
