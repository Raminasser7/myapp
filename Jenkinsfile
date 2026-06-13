pipeline {
    agent any

    environment {
        IMAGE_NAME = "myapp"
        DEPLOY_DIR = "/opt/myapp"
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'main',
                    credentialsId: 'myapp-rep-git-cred',
                    url: 'https://github.com/Raminasser7/myapp.git'
            }
        }

        stage('Build Image') {
            steps {
                sh "docker build -t ${IMAGE_NAME}:latest ."
            }
        }

        stage('Deploy') {
            steps {
                sh """
                    cd ${DEPLOY_DIR}
                    docker compose down
                    docker compose up -d
                """
            }
        }

    }
    
}
