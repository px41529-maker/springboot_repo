pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                 git branch: 'main',
                git 'https://github.com/px41529-maker/springboot_repo.git'
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run') {
            steps {
                sh 'nohup java -jar target/*.jar > app.log 2>&1 &'
            }
        }
    }
}
