pipeline {
    agent any

    stages {
        stage('Clone Repo') {
            steps {
                git branch: 'dev', url: 'https://github.com/Rockymca/devops-build.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t devops-react-app .'
            }
        }

        stage('Deploy Container') {
            steps {
                sh '''
                  docker stop react-container || true
                  docker rm react-container || true
                  docker run -d -p 3000:80 --name react-container devops-react-app
                '''
            }
        }
    }
}
