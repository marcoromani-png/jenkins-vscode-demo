// Carica la Shared Library configurata in Jenkins
@Library('my-shared-library') _

pipeline {
    // Esegue la pipeline su qualsiasi agente disponibile
    agent any


    // Inserimento dell'API-URL
    environment {
        API_URL = 'https://api.restful-api.dev/objects'
    }

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

        // Terzo stage: richiamo l'API
         /*stage('Call API endpoint') {
            steps {
                script {
                    echo "Chiamo API: ${API_URL}"

                    def response = httpRequest(
                        url: API_URL,
                        httpMode: 'GET',
                        acceptType: 'APPLICATION_JSON',
                        validResponseCodes: '200'
                    )

                    echo "Status code: ${response.status}"

                    echo 'Converto il body JSON in oggetto Groovy'
                    def body = readJSON text: response.content

                    echo 'Conto gli oggetti presenti nell array'
                    def countObjects = body.size()

                    echo "RISULTATO FINALE: l array contiene ${countObjects} oggetti"
                }
            }
        }*/



   
        stage('Call REST API') {
            steps {
                script {
                    def count = countApiObjects('https://api.restful-api.dev/objects')

                    //echo "L array contiene ${count} oggetti"
                }
            }
        }
    

        stage('Calculate Total Cost') {
            steps {
                script {
                    def totalCost = calculateTotalCost(API_URL)

                    //echo "Il costo totale degli oggetti è ${totalCost}"
                }
            }
        }



        // Quarto stage: simulazione della build
        stage('Build') {
            steps {
                echo 'Build del progetto demo'
            }
        }

        // Quinto stage: simulazione dei test
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






