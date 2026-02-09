pipeline {
    agent any

    parameters {
        choice(
            name: 'DEPLOY_ENV',
            choices: ['dev', 'qa'],
            description: 'Select environment'
        )
    }

    stages {

        stage('Build') {
            steps {
                bat "echo Building application..."
            }
        }

        stage('Auto Deployment in jenkins') {
            steps {
                bat "echo Auto deploying to %DEPLOY_ENV% environment"
            }
        }
    }
}

