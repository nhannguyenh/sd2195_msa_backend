pipeline {
    agent any
    stages {
        stage ("Build Image") {
            steps {
                sh ('docker build -t sd2195_ecr_backend .')
            }
        }
    }
}