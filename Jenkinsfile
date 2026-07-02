pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Repository recuperato correttamente'
            }
        }

        stage('Build') {
            steps {
                echo 'Simulazione build'
                sh 'ls -la'
            }
        }

        stage('Test') {
            steps {
                echo 'Simulazione test'
                sh 'echo Test eseguiti correttamente'
            }
        }
    }

    post {
        success {
            echo 'Pipeline completata con successo'
        }

        failure {
            echo 'Pipeline fallita'
        }
    }
}