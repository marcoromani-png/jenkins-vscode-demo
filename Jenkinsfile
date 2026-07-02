@Library('my-shared-library') _

pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                echo 'Checkout del repository applicativo completato'
            }
        }

        stage('Call Shared Library') {
            steps {
                sayHello()
            }
        }

        stage('Build') {
            steps {
                echo 'Build del progetto demo'
            }
        }

        stage('Test') {
            steps {
                echo 'Esecuzione test demo'
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