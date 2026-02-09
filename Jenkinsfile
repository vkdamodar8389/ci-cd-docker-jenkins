pipeline {
    agent any

    environment {
        APP_NAME = "ci-cd-docker-jenkins"
        DEPLOY_ENV = "dev"
    }

    stages {
        stage('CI Check') {
            steps {
                echo 'CI pipeline is running'
            }
        }

        stage('Docker Build') {
            steps {
                bat 'docker build -t ci-cd-demo .'
            }
        }

        stage('Deploy') {
            steps {
                withCredentials([string(credentialsId: 'demo-secret', variable: 'DEPLOY_TOKEN')]) {
                    bat '''
                    docker stop ci-cd-container || echo not running
                    docker rm ci-cd-container || echo not present
                    docker run --name ci-cd-container ci-cd-demo
                    '''
                }
            }
        }
    }
}

