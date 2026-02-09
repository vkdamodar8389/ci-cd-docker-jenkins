pipeline {
    agent any

    environment {
        IMAGE_NAME = "ci-cd-demo"
        CONTAINER  = "ci-cd-container"
    }

    stages {

        stage('CI') {
            steps {
                echo "CI running"
            }
        }

        stage('Build') {
            steps {
                bat "docker build -t %IMAGE_NAME% ."
            }
        }

        stage('Deploy') {
            steps {
                withCredentials([
                    usernamePassword(
                        credentialsId: 'demo-secret',
                        usernameVariable: 'USER',
                        passwordVariable: 'PASS'
                    )
                ]) {
                    bat '''
                    docker stop %CONTAINER% || echo not running
                    docker rm %CONTAINER% || echo not present
                    docker run -d --name %CONTAINER% %IMAGE_NAME%
                    '''
                }
            }
        }
    }
}

