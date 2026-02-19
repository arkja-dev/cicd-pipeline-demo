pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/arkja-dev/cicd-pipeline-demo.git'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t cicd-pipeline-demo .'
            }
        }

        stage('Run Docker Container') {
            steps {
                sh '''
                docker stop cicd-app || true
                docker rm cicd-app || true
                docker run -d -p 3000:3000 --name cicd-app cicd-pipeline-demo
                '''
            }
        }
    }
}
