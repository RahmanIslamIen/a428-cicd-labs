pipeline {
    agent {
        docker { image 'gradle:jdk11' }
    }
    stages {
        stage('Build Docker') {
            steps {
                sh 'curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh'
            }
        }
        stage('Build') { 
            steps {
                sh 'npm install'
            }
        }
        // Tambahkan tahapan lainnya di sini sesuai kebutuhan Anda
    }
    // Tambahkan bagian post success dan failure sesuai kebutuhan Anda
}
