pipeline {
    agent any

    stages {
        stage('Build App') {
            steps {
                sh 'node --version || echo Node not required here'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-pipeline-demo .'
            }
        }

        stage('Run Container') {
            steps {
                sh 'docker rm -f cicd-demo || true'
                sh 'docker run -d -p 3000:3000 --name cicd-demo cicd-pipeline-demo'
            }
        }
    }
}
