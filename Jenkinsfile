pipeline {
    stages {
        stage('Build Docker') {
            steps {
                sh 'curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh'
            }
        }
    }
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
    }
}
