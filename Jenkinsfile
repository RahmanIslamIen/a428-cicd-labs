pipeline {
    agent any
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Install') {
            steps {
                script {
                    env.PATH = "${tool(name: 'NodeJS', type: 'jenkins.plugins.nodejs.tools.NodeJSInstallation')}/bin:${env.PATH}"
                    sh 'npm install'
                }
            }
        }
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
    }
}
