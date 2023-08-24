pipeline {
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
        stage('Test') { 
            steps {
                sh './jenkins/scripts/test.sh' 
            }
        }
        stage('Deploy') {
            steps {
                // Lakukan tindakan yang diperlukan untuk deployment
                sh './jenkins/scripts/deploy.sh'
            }
        }
    }
    post {
        success {
            echo 'Pipeline succeeded! Deploying...'
            // Tindakan yang dilakukan jika pipeline sukses, misalnya notifikasi atau langkah berikutnya.
        }
        failure {
            echo 'Pipeline failed!'
            // Tindakan yang dilakukan jika pipeline gagal, misalnya notifikasi atau tindakan pemulihan.
        }
    }
}
