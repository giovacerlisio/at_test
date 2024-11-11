pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/giovacerlisio/at_test.git'
            }
        }

        stage('Install Dependencies') {
            steps {
                // Installazione delle dipendenze, per esempio tramite pip
                sh 'pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Esegui i test con pytest e salva i risultati in un formato compatibile con JUnit
                sh 'pytest test.py --junitxml=results.xml'
            }
        }
    }

    post {
        always {
            // Pubblica i risultati dei test
            junit 'results.xml'
        }
    }
}
