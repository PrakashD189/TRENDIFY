pipeline {
    agent any

    stages {

        stage('Clone Code') {
            steps {
                echo 'Code already fetched by Jenkins'
            }
        }

        stage('Build Docker Image') {
            steps {
                sh 'docker build -t trendify-app .'
            }
        }

        stage('Tag Image') {
            steps {
                sh 'docker tag trendify-app dprakash4a3/trendify-app'
            }
        }

        stage('Push to DockerHub') {
            steps {
                sh 'docker push dprakash4a3/trendify-app'
            }
        }

        stage('Deploy (Later)') {
            steps {
                echo 'Deployment to Kubernetes will be added later'
            }
        }
    }
}
