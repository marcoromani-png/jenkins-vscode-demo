// Carica la Shared Library configurata in Jenkins
@Library('my-shared-library') _

pipeline {
    // Esegue la pipeline su qualsiasi agente disponibile
    agent any

    // Elenco delle fasi della pipeline
    stages {

        // Primo stage: messaggio di checkout completato
        stage('Checkout') {
            steps {
                echo 'Checkout del repository applicativo completato'
            }
        }

        // Secondo stage: richiama una funzione della Shared Library
        stage('Call Shared Library') {
            steps {
                sayHello()
            }
        }

        // Terzo stage: simulazione della build
        stage('Build') {
            steps {
                echo 'Build del progetto demo'
            }
        }

        // Quarto stage: simulazione dei test
        stage('Test') {
            steps {
                echo 'Esecuzione test demo'
            }
        }
    }

    // Azioni da eseguire dopo la pipeline
    post {

        // Se tutto va bene
        success {
            echo 'Pipeline completata con successo'
        }

        // Se qualcosa fallisce
        failure {
            echo 'Pipeline fallita'
        }
    }
}