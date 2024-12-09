pipeline {
    agent any
    stages {
        stage ("Build image") {
            steps {
                sh ('docker build -t sd2195_ecr_backend .')
            }
        }
        stage ("Push image") {
            steps {
                sh ('aws ecr get-login-password --region ap-southeast-1 | docker login --username AWS --password-stdin 211125338837.dkr.ecr.ap-southeast-1.amazonaws.com')
                sh ('docker tag sd2195_ecr_backend:latest 211125338837.dkr.ecr.ap-southeast-1.amazonaws.com/sd2195_ecr_backend:latest')
                sh ('docker push 211125338837.dkr.ecr.ap-southeast-1.amazonaws.com/sd2195_ecr_backend:latest')
            }
        }
    }
}