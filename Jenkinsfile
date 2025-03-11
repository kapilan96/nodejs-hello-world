pipeline {
    agent any  

    environment {
        NODE_VERSION = "20"
    }

    tools {
        nodejs "nodejs-${NODE_VERSION}"  
    }

    stages {
        stage('Setup Node.js') {
            steps {
                script {
                    def nodeHome = tool name: "nodejs-${NODE_VERSION}", type: "jenkins.plugins.nodejs.tools.NodeJSInstallation"
                    env.PATH = "${nodeHome}/bin:${env.PATH}"
                }
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