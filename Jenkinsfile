pipeline {
    agent any

    parameters {
        choice(
            name: 'DEPLOY_ENV',
            choices: ['dev', 'qa', 'prod'],
            description: 'Select environment'
        )
    }

    stages {

        stage('Build') {
            steps {
                bat "echo Building application..."
            }
        }

        stage('Auto Deploy (DEV / QA)') {
            when {
                expression {
                    params.DEPLOY_ENV == 'dev' || params.DEPLOY_ENV == 'qa'
                }
            }
            steps {
                bat "echo Auto deploying to %DEPLOY_ENV% environment"
            }
        }

        stage('Manual Approval (PROD)') {
            when {
                expression { params.DEPLOY_ENV == 'prod' }
            }
            steps {
                input message: 'Approve PROD deployment?', ok: 'Deploy'
            }
        }

        stage('Deploy to PROD') {
            when {
                expression { params.DEPLOY_ENV == 'prod' }
            }
            steps {
                bat "echo Deploying to PROD environment"
            }
        }
    }
}

