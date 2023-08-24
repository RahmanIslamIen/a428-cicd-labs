pipeline {
    agent any
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
