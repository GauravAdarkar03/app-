pipeline {
    agent any

    environment {
        IMAGE_NAME = "my-docker-app"
    }

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t $IMAGE_NAME .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker stop my-container || true
                docker rm my-container || true
                docker run -d -p 8081:80 --name my-container $IMAGE_NAME
                '''
            }
        }

    }

}
