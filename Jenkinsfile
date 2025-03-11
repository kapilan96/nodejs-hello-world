pipeline {
    agent any

    stages {
        stage('Check npm path') {
            steps {
                sh 'which npm'
                sh 'npm -v'
            }
        }

        stage('Install dependencies') {
            steps {
                script {
                    env.PATH = "${env.PATH}:/opt/homebrew/bin"
                }
                sh 'npm install'
            }
        }

        stage('Run tests') {
            steps {
                script {
                    env.PATH = "${env.PATH}:/opt/homebrew/bin"
                }
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