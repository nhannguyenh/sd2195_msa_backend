pipeline {
    agent any

    environment {
        AWS_ACCOUNT_ID = '211125338837'
        AWS_DEFAULT_REGION = 'ap-southeast-1'
        IMAGE_REPO_NAME = 'sd2195_ecr_backend'
        IMAGE_TAG = 'latest'
        REPOSITORY_URI = '${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com/${IMAGE_REPO_NAME}'
    }

    stages {
        stage ("Build image") {
            steps {
                sh ('docker build -t ${IMAGE_REPO_NAME} .')
            }
        }
        stage ("Push image") {
            steps {
                sh ('aws ecr get-login-password --region ${AWS_DEFAULT_REGION} | docker login --username AWS --password-stdin ${AWS_ACCOUNT_ID}.dkr.ecr.${AWS_DEFAULT_REGION}.amazonaws.com')
                sh ('docker tag ${IMAGE_REPO_NAME}:${IMAGE_TAG} ${REPOSITORY_URI}:${IMAGE_TAG}')
                sh ('docker push ${REPOSITORY_URI}:${IMAGE_TAG}')
            }
        }
    }
}