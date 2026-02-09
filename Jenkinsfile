pipeline {
    agent any

    parameters {
        choice(
            name: 'DEPLOY_ENV',
            choices: ['dev', 'qa', 'prod'],
            description: 'Select environment to deploy'
        )

        booleanParam(
            name: 'RUN_DEPLOY',
            defaultValue: true,
            description: 'Enable deployment stage'
        )
    }

    stages {
        stage('Print Parameters') {
            steps {
                bat """
                echo Environment Selected: %DEPLOY_ENV%
                echo Deployment Enabled: %RUN_DEPLOY%
                """
            }
        }
    }
}

