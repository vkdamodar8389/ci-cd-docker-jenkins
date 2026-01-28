pipeline {
    agent any

    stages {
        stage('CI Check') {
            steps {
                echo 'CI pipeline is running'

	stage('Docker Build') {
	     steps {
	            bat 'Docker build -t ci-cd-demo .'

            }
        }
    }
}

