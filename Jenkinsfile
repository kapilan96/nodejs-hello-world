pipeline {
    agent any  // Définit un agent pour exécuter le pipeline

    tools {
        nodejs "NodeJS"  // ✅ Change "NodeJS 20.0.0" par "NodeJS"
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