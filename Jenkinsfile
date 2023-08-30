pipeline {
    agent {
        docker {
            image 'node:16-buster-slim' 
            args '-p 3000:3000' 
        }
    }
    stages {
        // stage('Preparation') {
        //     steps {
        //         sh 'npm cache clean --force'
        //     }
        // }
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh './jenkins/scripts/test.sh'
            }
        }
        // stage('Deploy') {
        //     steps {
        //         sh './jenkins/scripts/deliver.sh'
        //          input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
        //          sleep 1 * 60
        //         sh './jenkins/scripts/kill.sh'
        //     }
        // }
    }
}
