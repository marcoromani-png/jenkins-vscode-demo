// Carica la Shared Library configurata in Jenkins
@Library('my-shared-library') _


// Variabili condivise tra gli stage
def episodes = []
def characterStats = [:]


pipeline {
    // Esegue la pipeline su qualsiasi agente disponibile
    agent any


    // Inserimento dell'API-URL
    environment {
        API_URL = 'https://api.restful-api.dev/objects'
        EPISODES_API_URL = 'https://api.attackontitanapi.com/episodes'

    }

    // Elenco delle fasi della pipeline
    stages {

        // Primo stage: messaggio di checkout completato
        stage('Checkout') {
            steps {
                echo 'Checkout del repository applicativo completato'
            }
        }



        stage('Get all episodes') {
            steps {
                script {
                    echo 'Recupero episodi'

                    episodes = getAllEpisodes(env.EPISODES_API_URL)

                    echo "Totale episodi recuperati: ${episodes.size()}"
                }
            }
        }





        stage('Count characters in episodes') {
            steps {
                script {
                    echo 'Conteggio characters'

                    characterStats = countCharactersInEpisodes(episodes)

                    echo "Totale character distinti trovati: ${characterStats.size()}"
                }
            }
        }



   
   
        stage('Print result') {
            steps {
                script {
                    echo 'Stampa risultato finale'

                    for (characterUrl in characterStats.keySet()) {

                        def data = characterStats[characterUrl]

                        echo "Character: ${data.name}"
                        echo "Compare in episodi: ${data.count}"
                    }
                }
            }
        }





   
        /*stage('Call REST API') {
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
        }*/
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






