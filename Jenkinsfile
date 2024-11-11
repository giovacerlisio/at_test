pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git 'https://github.com/giovacerlisio/at_test.git'
            }
        }

        stage('Setup Python Virtual Environment') {
            steps {
                // Creare un ambiente virtuale
                sh 'python3 -m venv venv'

                // Attivare l'ambiente virtuale e installare le dipendenze
                sh './venv/bin/pip install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Eseguire i test all'interno dell'ambiente virtuale
                sh './venv/bin/python -m pytest test.py --junitxml=results.xml'
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
