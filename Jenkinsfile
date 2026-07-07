pipeline {
    agent any

    environment {
        IMAGE_NAME = "newspringboot-app"
        IMAGE_TAG = "v1"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/px41529-maker/springboot_repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Docker Build') {
            steps {
                sh 'docker build -t ${IMAGE_NAME}:${IMAGE_TAG} .'
            }
        }

        stage('Run Container') {
            steps {
                sh '''
                docker rm -f springboot-container || true

                docker run -d \
                  --name springboot-container \
                  -p 5000:9090 \
                  ${IMAGE_NAME}:${IMAGE_TAG}
                '''
            }
        }
    }
}
