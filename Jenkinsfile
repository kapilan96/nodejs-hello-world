pipeline {
    agent any  // Assure l'exécution sur n'importe quel agent

    tools {
        nodejs "NodeJS 20.0.0"  // Utilise le même nom que celui défini dans Jenkins
    }

    stages {
        stage('Check NodeJS') {
            steps {
                sh 'node -v'
                sh 'npm -v'
            }
        }

        stage('Install dependencies') {
            steps {
                sh 'npm install'
            }
        }

        stage('Run tests') {
            steps {
                sh 'npm test'
            }
        }
    }

    post {
        always {
            echo 'Nettoyage post-build...'
            sh 'rm -rf node_modules'
        }
    }
}