pipeline {
    agent any

    stages {

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t trendify-app .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag trendify-app dprakash4a3/trendify-app:${BUILD_NUMBER}'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push dprakash4a3/trendify-app:${BUILD_NUMBER}'
            }
        }

        stage('Deploy to Kubernetes') {
            steps {
                sh '''
                kubectl set image deployment/trendify-deployment trendify-container=dprakash4a3/trendify-app:${BUILD_NUMBER}
                '''
            }
        }
    }
}
