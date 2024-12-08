pipeline {
    agent any
    stages {
        stage ("Checkout") {
            checkout scmGit(
                branches: [[name: '*/main']],
                extensions: [],
                userRemoteConfigs: [[url: 'https://github.com/nhannguyenh/sd2195_msa_backend.git']]
            )
        }
        stage ("Build Image") {
            steps {
                sh ('docker build -t backend .')
            }
        }
    }
}