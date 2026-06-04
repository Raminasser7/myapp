pipeline {
    agent any
    stages {
        stage('Pull Code') {
            steps {
                git branch: 'main',
                    credentialsId: 'myapp-rep-git-cred',
                    url: 'https://github.com/Raminasser7/myapp.git'
            }
        }
        stage('Build Image') {
            steps {
                sh 'docker build -t myapp /var/jenkins_home/workspace/myapp'
            }
        }
        stage('Deploy') {
            steps {
                sh '''
                    cd /var/jenkins_home/workspace/myapp
                    docker compose down
                    docker compose up -d --build
                '''
            }
        }
    }
}
