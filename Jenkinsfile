pipeline {
    environment {
        NODE_VERSION = "20"
    }

    stages {
        stage('Setup Node.js') {
            steps {
                script {
                    def nodeHome = tool name: "nodejs-${NODE_VERSION}", type: "jenkins.plugins.nodejs.tools.NodeJSInstallation"
                    env.PATH = "${nodeHome}/bin:${env.PATH}"
                }
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