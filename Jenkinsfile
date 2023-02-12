pipeline {
    agent any

    environment {
        REGISTRY_URL = '700935310038.dkr.ecr.eu-north-1.amazonaws.com'
        IMAGE_NAME = 'aleksei1988-yolo5'
    }

    stages {
        stage('Build') {
            steps {
                sh '''
                aws ecr get-login-password --region eu-north-1 | docker login --username AWS --password-stdin $REGISTRY_URL
                docker build -t $IMAGE_NAME:$BUILD_NUMBER .
                docker tag $IMAGE_NAME:$BUILD_NUMBER $REGISTRY_URL/$IMAGE_NAME:$BUILD_NUMBER
                docker push $REGISTRY_URL/$IMAGE_NAME:$BUILD_NUMBER
                '''
            }
        }
    }
}