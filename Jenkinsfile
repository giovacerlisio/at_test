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
                // Usa pip3 per installare le dipendenze
                sh 'pip3 install -r requirements.txt'
            }
        }

        stage('Run Tests') {
            steps {
                // Esegui i test con python3 e pytest
                sh 'python3 -m pytest test.py --junitxml=results.xml'
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
