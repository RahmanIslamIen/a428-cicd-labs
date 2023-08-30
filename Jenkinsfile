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
        // ngebuat stage baru Manual Approval sebelum di Deploy.
        stage('Manual Approval') {
            steps {
                script {
                    def userInput = input(
                        id: 'manual-approval',
                        message: 'Lanjutkan ke tahap Deploy?',
                        parameters: [
                            choice(choices: ['lanjut', 'batal'], description: 'Pilih opsi:', name: 'approval')
                        ]
                    )
                    if (userInput == 'batal') {
                        error('Pipeline di berhentikan oleh pengguna/user.')
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                sh './jenkins/scripts/deliver.sh'
                //  input message: 'Sudah selesai menggunakan React App? (Klik "Proceed" untuk mengakhiri)'
                sleep 1 * 60
                sh './jenkins/scripts/kill.sh'
            }
        }
    }
}
